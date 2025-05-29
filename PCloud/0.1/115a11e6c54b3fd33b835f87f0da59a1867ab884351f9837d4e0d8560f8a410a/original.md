```
lostpassword(client::PCloudClient; kwargs...)
```

Change current user's password

Takes as a parameter user's `mail` and sends to this email address insertuctions and link to reset user's password.

Successful reply is sent even if there is no user of the system with `mail` for security reasons.

Source: https://docs.pcloud.com/methods/auth/lostpassword.html

# Arguments

  * `mail::String`: e-mail of the user, where instructions are sent

# Output Example

```
{
    "result": 0
}
```
