```
UA_Client_connect(client::Ptr{UA_Client}, endpointurl::AbstractString)::UA_StatusCode
```

`client`を`endpointurl`でサーバーに接続します。これは匿名接続であり、ユーザー名やパスワードは使用されません（一部のサーバーではこれを許可していません）。
