```
changemail(client::PCloudClient; kwargs...)
```

Change current user's email. Takes `newmail` from `code`.

Source: https://docs.pcloud.com/methods/auth/changemail.html

# Arguments

  * `password::String`: current password of the user
  * `code::String`: code sent in email

# Output Example

```
{
    "result": 0
}
```
