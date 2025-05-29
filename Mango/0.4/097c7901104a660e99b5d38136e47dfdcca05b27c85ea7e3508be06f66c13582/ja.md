```
create_mqtt_container(host, port, client_id; codec=nothing)
```

MQTTプロトコルを使用してコンテナを作成します。

`host`はブローカーのIPアドレスであることが期待され、`port`はブローカーのポート、`client_id`はブローカーに接続されるクライアントのIDです。オプションで、関数のタプルとしてコーデックを提供することもできます（最初はエンコード、2番目はデコード、参照は[`encode`](@ref)および[`decode`](@ref)を参照）。

# 例

```julia
agent = create_mqtt_container("127.0.0.1", 5555, "MyClient")
```
