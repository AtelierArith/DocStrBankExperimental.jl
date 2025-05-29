```
newsletter_check(client::PCloudClient; kwargs...)
```

Checks if the current logged usre is subscribed to pCloud Newsletter.

Source: https://docs.pcloud.com/methods/newsletter/newsletter_check.html

# Output

The filed `subscribed` is `true`, if the user was subscribed to the Newsletter.

The field `verified` is `true`, if the user had already verified his email, using a link, sent in a mail to his email address.

# Output Example

```
{
    subscribed: true,
    verified: false,
    result: 0
}
```
