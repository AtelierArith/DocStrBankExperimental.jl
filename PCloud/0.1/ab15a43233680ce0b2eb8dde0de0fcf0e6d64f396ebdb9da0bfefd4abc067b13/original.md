```
sendchangemail(client::PCloudClient; kwargs...)
```

Sends email to the logged in user with link.

If you send `newmail` and `code`, sends email to `newmail` with link to last step.

Source: https://docs.pcloud.com/methods/auth/sendchangemail.html

# Optional Arguments

  * `newmail::String`: newemail of the user
  * `code::String`: code sent in email

# Output Example

```
{
    "result": 0
}
```
