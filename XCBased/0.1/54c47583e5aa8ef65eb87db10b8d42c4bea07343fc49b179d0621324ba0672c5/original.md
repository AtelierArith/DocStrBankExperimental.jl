```
get_maximum_request_length(conn:: XCBConnection) -> UInt32
```

From the XCB documentation:

> In the absence of the BIG-REQUESTS extension, returns the maximum request length field from the connection setup data, which may be as much as 65535. If the server supports BIG-REQUESTS, then the maximum request length field from the reply to the BigRequestsEnable request will be returned instead.
>
> Note that this length is measured in four-byte units, making the theoretical maximum lengths roughly 256kB without BIG-REQUESTS and 16GB with.

