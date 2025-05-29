```
currentserver(client::PCloudClient; kwargs...)
```

Returns `ip` and `hostname` of the server you are currently connected to. The hostname is guaranteed to resolve only to the IP address(es) pointing to the same server. This call is useful when you need to track the upload progress.

Source: https://docs.pcloud.com/methods/general/currentserver.html

# Output

  * `ip::String`: IP v.4 address of the server
  * `ipbin::String`: IP v.4 address
  * `ipv6::String`: IP v.6 address of the server
  * `hostname::String`: hostname of the server

# Output Example

```
{
    ipv6: "::1",
    hostname: "api7.pcloud.com",
    ip: "204.155.155.21",
    result: 0,
    ipbin: "204.155.155.60"
}
```
