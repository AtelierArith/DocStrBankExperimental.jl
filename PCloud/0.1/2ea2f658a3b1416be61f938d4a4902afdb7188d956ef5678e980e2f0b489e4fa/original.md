```
declineshare(client::PCloudClient; kwargs...)
```

Decline a share request.

The request can be either identified by `sharerequestid` as reported by diff or by a `code` that comes from email.

If the optional parameter `block` is set, all future share requests from the offering user will be automatically declined.

Source: https://docs.pcloud.com/methods/sharing/declineshare.html

# Arguments

  * `sharerequestid::Int`: The id of the share request
  * `code::String`: The code that was sent to the user's email

Use `sharerequestid` or `code`.

# Optional Arguments

  * `block::Int`: If set, all future share requests from the offering user will be automatically declined.

# Output Example

```
{
    "result": 0
}
```
