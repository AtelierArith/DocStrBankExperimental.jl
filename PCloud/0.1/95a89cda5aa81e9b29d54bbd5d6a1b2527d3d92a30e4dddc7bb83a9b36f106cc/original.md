```
newsletter_verifyemail(client::PCloudClient; kwargs...)
```

Uses a `code` sent in a mail to the email, which the user had subscribed to the Newsletter. If the `code` is valid, then the user's email is marked as verified.

Source: https://docs.pcloud.com/methods/newsletter/newsletter_verifyemail.html

# Arguments

  * `code::String`: code, sent in a mail to the user

# Output

The `email` that was marked as verified is set This is for security reasons.

# Output Example

```
{
    result: 0,
    email: "newsletter@pcloud.com"
}
```
