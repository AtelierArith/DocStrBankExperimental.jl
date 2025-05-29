```
response::Ptr{Open62541.UA_QueryNextResponse)} = UA_Client_Service_queryNext(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_QueryNextResponse)})
```

クライアントの queryNext サービス API を使用して、以前に定義された `request` に対して `response` を提供します。レスポンスのメモリは C によって割り当てられ、使用後に `UA_QueryNextResponse_delete(response)` を使用してクリーンアップする必要があります。

!!! これは open62541 内の低レベルの関数です。通常は、より特定的で高レベルの関数を使用する方がはるかに良く、便利です。

関連情報:

[`Open62541.UA_QueryNextResponse`](@ref)

[`Open62541.UA_QueryNextRequest`](@ref)
