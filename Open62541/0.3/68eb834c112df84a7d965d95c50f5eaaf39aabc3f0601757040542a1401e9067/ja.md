```
response::Ptr{Open62541.UA_WriteResponse)} = UA_Client_Service_write(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_WriteResponse)})
```

クライアントの書き込みサービスAPIを使用して、以前に定義された`request`に`response`を提供します。`response`のメモリはCによって割り当てられ、使用後に`UA_WriteResponse_delete(response)`を使用してクリーンアップする必要があります。

!!! これはopen62541内の低レベルの関数です。通常は、より特定的で高レベルの関数を使用する方がはるかに良く、便利です。

関連情報:

[`Open62541.UA_WriteResponse`](@ref)

[`Open62541.UA_WriteRequest`](@ref)
