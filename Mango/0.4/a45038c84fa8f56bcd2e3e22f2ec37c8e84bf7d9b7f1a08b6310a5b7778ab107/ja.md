```
create_tcp_container(host, port; codec=nothing)
```

TCPプロトコルを使用してコンテナを作成します。

`host`はバインドするIPアドレスであることが期待され、`port`はバインドするポートです。オプションで、関数のタプル（最初はエンコード、2番目はデコード）としてコーデックを提供することもできます（[`encode`](@ref)および[`decode`](@ref)を参照）。

# 例

```julia
agent = create_mqtt_container("127.0.0.1", 5555, "MyClient")
```
