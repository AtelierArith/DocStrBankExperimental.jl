```
getip(client::PCloudClient; kwargs...)
```

Get the IP address of the remote device from which the user connects to the API.

Source: https://docs.pcloud.com/methods/general/getip.html

# Output

Returns `ip` - the remote address of the user that is connecting to the API.

Also, returns `country` - lowercase two-letter code of the country that is defined according to the remote address. If the country could not be defined, then this fields is `false`.

# Output Example

```
{
  "result": 0,
  "ip": "127.0.0.1",
  "country": "gb"
  ]
}
```
