```
response::Ptr{Open62541.UA_ReadResponse)} = UA_Client_Service_read(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_ReadResponse)})
```

クライアントの読み取りサービスAPIを使用して、以前に定義された`request`に対して`response`を提供します。レスポンスのメモリはCによって割り当てられ、使用後に`UA_ReadResponse_delete(response)`を使用してクリーンアップする必要があります。

!!! これはopen62541内の低レベルの関数です。通常は、より特定的で高レベルの関数を使用する方がはるかに良く、便利です。

関連情報:

[`Open62541.UA_ReadResponse`](@ref)

[`Open62541.UA_ReadRequest`](@ref)
