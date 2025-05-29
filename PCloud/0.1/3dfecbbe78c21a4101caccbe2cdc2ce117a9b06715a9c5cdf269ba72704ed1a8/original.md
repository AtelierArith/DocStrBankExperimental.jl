```
newsletter_unsubscribe(client::PCloudClient; kwargs...)
```

Uses a `code` sent in a mail to the email, which the user had subscribed to the Newsletter. If the `code` is valid, then the user's email is unsubscribed.

Source: https://docs.pcloud.com/methods/newsletter/newsletter_unsubscribe.html

# Arguments

  * `code::String`: code, sent in a mail to the user

# Output

Always sends `result`=0, even if the user was never added to the Newsletter. This is for security reasons.

# Output Example

```
{
    result: 0
}
```
