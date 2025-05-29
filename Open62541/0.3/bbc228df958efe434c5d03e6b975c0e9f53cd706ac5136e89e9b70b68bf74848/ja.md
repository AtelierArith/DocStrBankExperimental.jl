```
response::Ptr{Open62541.UA_BrowseResponse)} = UA_Client_Service_browse(client::Ptr{UA_Client}, request::Ptr{Open62541.UA_BrowseResponse)})
```

クライアントのブラウズサービスAPIを使用して、以前に定義された`request`に対する`response`を提供します。レスポンスのメモリはCによって割り当てられ、使用後に`UA_BrowseResponse_delete(response)`を使用してクリーンアップする必要があります。

!!! これはopen62541内の低レベルの関数です。通常は、より特定的で高レベルの関数を使用する方がはるかに良く、便利です。

関連情報:

[`Open62541.UA_BrowseResponse`](@ref)

[`Open62541.UA_BrowseRequest`](@ref)
