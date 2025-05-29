```
getapiserver(client::PCloudClient; kwargs...)
```

This method returns closest API server to the requesting client. The biggest speed gain will be with upload methods. Clients should have fallback logic. If request to API server different from api.pcloud.com fails (network error) the client should fallback to using api.pcloud.com.

Source: https://docs.pcloud.com/methods/general/getapiserver.html

# Output

binapi - array with API servers that support connections via pCloud's binary protocol

api - array with API servers that support connections via HTTP/HTTPS protocol

# Output Example

```
{
  "result": 0,
  "binapi": [
    "binapi-ams1.pcloud.com"
  ],
  "api": [
    "api-ams1.pcloud.com"
  ]
}
```
