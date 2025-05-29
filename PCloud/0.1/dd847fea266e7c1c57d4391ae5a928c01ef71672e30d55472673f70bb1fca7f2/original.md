```
changepassword(client::PCloudClient; kwargs...)
```

Change current user's password

Takes `oldpassword` that must contain user's old password and `newpassword` and changes user's password.

New password should be at least 6 characters in length, contain at least 4 different characters, cannot be all consecutive characters (either alphabet or numbers, neither of the following is valid 'abcdef', '123456', '987654') and cannot be all consecutive letters from a standard keyboard (no 'qwerty' or 'poiuyt'). Also the password can not start or end with whitespace.

Source: https://docs.pcloud.com/methods/auth/changepassword.html

# Arguments

  * `oldpassword::String`: current password of the user
  * `newpassword::String`: the wished password that will overwrite the current

# Output Example

```
{
    "result": 0
}
```
