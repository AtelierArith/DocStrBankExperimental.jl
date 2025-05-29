```
newsletter_unsubscribemail(client::PCloudClient; kwargs...)
```

Sends an email to the given `mail` with a code, that could be used to unsubcribe the email from the Newsletter.

This email is sent to a `mail` that was added to the newsletter, but it is not necessary to be verified.

Source: https://docs.pcloud.com/methods/newsletter/newsletter_unsibscribemail.html

# Arguments

  * `code::String`: code, sent in a mail to the user

# Output

Always sends `result`=0, even if the email was never sent. This is for security reasons.

# Output Example

```
{
    result: 0
}
```
