# ServiceAccountManager
Manage passwords and reset policies on web service accounts in ServiceNow
Roles
N/A the same role logic as your sys_user table

Navigation
Navigate to User Administration -> Users | Filter Web Service Access Only = True

Fields
Lower Case	True | False determine whether the generated password should contain lowercase characters
Upper Case	True | False determine whether the generated password should contain uppercase characters
Number	True | False determine whether the generated password should contain numbers
Special Character	True | False determine whether the generated password should contain special characters
Application	Reference to the cmdb_ci_appl table to allow better tracking of what this service account is used for
Length	Integer determine how long the generate password should be
Last Password Change	Date Time | Read Only this is auto populated when the service accounts password has been changed
Service Account Manager fields on sys_user Table
Example
The current settings for this service account are as follows



Click Generate Password UI Action:


Now you can copy the password and paste it into the password field as well as notify the team of their new password manually this can also be configured to be performed automatically via the custom Flow.

Role(s)
flow_designer

flow_designer_scripting

Navigation
Navigate to Process Automation -> Flow Designer | Filter Application = ServiceAccount

Flows
Service Account Password Change Reminder
Every week on Monday 10AM System Time the flow will evaluate all web service user accounts to determine whether a reminder email should be sent to them based on the last password change date.

The wording of the email and the frequency/duration of the emails that should be received can be tweaked on this flow.

The OOB Wording and logic is based off a 60 day expiration policy for the passwords.

Expired Service Account Password
Every day at 1 AM System Time the flow checks for web service user accounts whose passwords has expired (older than 60 days).

The flow proceeds to change the accounts password and emails the owner (sys_user.email) of the account to inform that the password for the account will be changed.

A second email is sent to the same email with the new password.
