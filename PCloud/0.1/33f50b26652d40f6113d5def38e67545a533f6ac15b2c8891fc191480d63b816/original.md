```
newsletter_subscribe(client::PCloudClient; kwargs...)
```

Subscribes an email for pCloud Newsletter.

If the email was not already verified, then a link is sent in the mail. After using the link, the email owner will verify his email.

Source: https://docs.pcloud.com/methods/newsletter/newsletter_subscribe.html

# Arguments

  * `mail::String`: the mail that is eneterd to the Newsletter list

# Output

In the filed `verifymail` is `true` if a verify mail is sent.

# Output Example

```
{
    verifymail: true,
    result: 0
}
```
