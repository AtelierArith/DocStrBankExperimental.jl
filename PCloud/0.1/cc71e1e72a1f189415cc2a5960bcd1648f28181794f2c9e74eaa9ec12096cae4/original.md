```
register(client::PCloudClient; kwargs...)
```

Register a new user account

Parameter `termsaccepted` MUST be set to `yes` if the user accepted terms of service and other agreements.

The new password is subject to the same checks as in changepassword.

Source: https://docs.pcloud.com/methods/auth/register.html

# Arguments

  * `mail::String`: user's email address
  * `password::String`: the password chosen by the user

# Optional Arguments

  * `language::String`: set to one of the supported languages. See supportedlanguages
  * `referer::String`: the userid of the refering user

# Output Example

```
{
    "result": 0
}
```
