```
userinvites(client::PCloudClient; kwargs...)
```

Get a list of the invitations of the current user.

Source: https://docs.pcloud.com/methods/auth/userinvites.html

# Output

Returns a list `invites` containing information about the accepted invitations. It has the format:

  * `email::String`: the email of the inivted user. For security, part of the mail is hidden.
  * `is_pending::Bool`: is the inivitation pending.

New user is added to this list when the invited user is registered and is not pending when the user validates his mail.

# Output Example

```
{
    "invites": [
    {
        "email": "x**@xyz.com",
        "is_pending": 1
    },

    ...

    ] , 
    result: 0
}
```
