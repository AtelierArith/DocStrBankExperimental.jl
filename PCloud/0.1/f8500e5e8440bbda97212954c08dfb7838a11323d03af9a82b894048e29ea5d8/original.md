```
invite(client::PCloudClient; kwargs...)
```

Get url of a registration page with a referrer code that credits free space to user account upon user registration.

Source: https://docs.pcloud.com/methods/auth/invite.html

# Output

  * `url::String`: address of the registration page
  * `spacelimitreached::Bool`: is the maximum of free space is reached by the user or not.

# Output Example

```
{
    url: "https://my.pcloud.com/#page=register&invite=invite_code",
    spacelimitreached: false,
    result: 0
}
```
