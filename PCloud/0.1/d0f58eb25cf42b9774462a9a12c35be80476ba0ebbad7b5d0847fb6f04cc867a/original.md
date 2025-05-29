```
verifyemail(client::PCloudClient; kwargs...)
```

Verify an email

Expects parameter `code` that is the activation code sent in validation emails.

In case of valid code, validates user's email address and returns `email` and `userid` of the verified user.

Please keep in mind that the code might be for a user, different than the currently logged one (if any).

Source: https://docs.pcloud.com/methods/auth/verifyemail.html

# Arguments

  * `code::String`: activation code sent in validation emails

# Output

  * `email::String`: email of the user
  * `userid::Int`: id of the user

# Output Example

```
{
    "result": 0,
    "email": "pcloud@pcloud.com",
    "userid": 1234
}
```
