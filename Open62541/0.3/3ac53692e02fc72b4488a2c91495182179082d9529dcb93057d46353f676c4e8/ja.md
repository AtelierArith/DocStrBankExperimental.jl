```
Open62541.UA_EndpointDescription_copy(src::Ptr{Open62541.UA_EndpointDescription}, dst::Ptr{Open62541.UA_EndpointDescription})::UA_STATUSCODE
Open62541.UA_EndpointDescription_copy(src::Open62541.UA_EndpointDescription, dst::Ptr{Open62541.UA_EndpointDescription})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容を宛先オブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
