```
changeshare(client::PCloudClient; kwargs...)
```

Change permissions of a share.

The permissions are the same as in sharefolder

Only the owner of the share/folder may use this method.

That is - it is only allowed for

*outgoing* shares.

Source: https://docs.pcloud.com/methods/sharing/changeshare.html

# Arguments

  * `shareid::Int`: The id of the share request, returned by listshares
  * `permissions::String`: The new permissions

# Output Example

```
{
    "result": 0
}
```
