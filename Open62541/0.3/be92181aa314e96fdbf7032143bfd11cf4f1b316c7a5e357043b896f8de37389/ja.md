```
response::Ptr{Open62541.UA_AddNodesResponse)} = UA_Client_Service_addNodes(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_AddNodesResponse)})
```

クライアントの addNodes サービス API を使用して、以前に定義された `request` に `response` を提供します。レスポンスのメモリは C によって割り当てられ、使用後に `UA_AddNodesResponse_delete(response)` を使用してクリーンアップする必要があります。

!!! これは open62541 内の低レベルの関数です。通常は、より具体的で高レベルの関数を使用する方がはるかに良く、便利です。

関連情報:

[`Open62541.UA_AddNodesResponse`](@ref)

[`Open62541.UA_AddNodesRequest`](@ref)
