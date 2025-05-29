```
JUA_Client_connectUsername(client::JUA_Client, endpointurl::AbstractString, 
    username::AbstractString, password::AbstractString)::UA_StatusCode
```

は、`client`をエンドポイントURL `endpointurl`を持つサーバーに接続し、`username`と`password`をログイン資格情報として提供します。
