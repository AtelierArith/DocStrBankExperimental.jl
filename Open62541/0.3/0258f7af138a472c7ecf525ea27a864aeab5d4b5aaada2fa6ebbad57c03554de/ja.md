```
JUA_Client_connect(client::JUA_Client, endpointurl::AbstractString)::UA_StatusCode
```

`client`を`endpointurl`のサーバーに接続します。これは匿名接続であり、ユーザー名やパスワードは使用されません（一部のサーバーではこれを許可していません）。
