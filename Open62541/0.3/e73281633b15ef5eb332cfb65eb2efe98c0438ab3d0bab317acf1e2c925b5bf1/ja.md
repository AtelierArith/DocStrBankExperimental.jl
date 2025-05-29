```
UA_Client_connectUsername(client::Ptr{UA_Client}, endpointurl::AbstractString, 
    username::AbstractString, password::AbstractString)::UA_StatusCode
```

は、`client`をエンドポイントURL `endpointurl`を持つサーバーに接続し、ログイン資格情報として`username`と`password`を提供します。
