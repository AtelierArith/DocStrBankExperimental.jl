```
logout(client::PCloudClient; kwargs...)
```

Gets a `token` and invalidates it.

Source: https://docs.pcloud.com/methods/auth/logout.html

# Output

Returns bool `auth_deleted` if the `token` invalidation was successful

(token was correct and it was actually invalidated).

# Output Example

```
{
    result: 0,
    auth_deleted: true
}
```
