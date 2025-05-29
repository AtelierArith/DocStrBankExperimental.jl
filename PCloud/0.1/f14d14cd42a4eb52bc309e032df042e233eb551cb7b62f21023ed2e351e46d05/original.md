```
feedback(client::PCloudClient; kwargs...)
```

Sends message to pCloud support

Source: https://docs.pcloud.com/methods/general/feedback.html

# Arguments

  * `mail::String`: email of the user
  * `reason::String`: subject of the request
  * `message::String`: the message itself

# Optional Arguments

  * `name::String`: can be provided with users full name

# Output Example

```
{
    result: 0
}
```
