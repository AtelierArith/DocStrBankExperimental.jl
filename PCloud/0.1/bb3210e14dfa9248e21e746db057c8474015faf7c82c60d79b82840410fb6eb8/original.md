```
resetpassword(client::PCloudClient; kwargs...)
```

Reset user's password

Expect as parameters `code` as sent in email in lostpassword

Resets user's password to `newpassword`.

The new password is subject to the same checks as in changepassword.

Source: https://docs.pcloud.com/methods/auth/resetpassword.html

# Arguments

  * `code::String`: code sent to the user in lostpassword
  * `newpassword::String`: the new password of the user

# Output Example

```
{
    "result": 0
}
```
