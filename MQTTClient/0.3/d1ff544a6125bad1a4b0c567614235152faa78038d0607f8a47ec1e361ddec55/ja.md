```
connect_async(client::Client, connection::Connection)
```

指定された `Client` および `Connection` オブジェクトを使用して、MQTT ブローカーへの非同期接続を確立します。この関数はクライアントを初期化し、接続を確立し、通信のために必要なループを開始します。

# 引数

  * `client::Client`: MQTT クライアントインスタンス。
  * `connection::Connection`: ブローカーに接続するために使用される接続情報。

# 戻り値

  * 接続プロセスの完了を待機するために使用できる `Future` オブジェクト。

## 例

```julia
client, connection = MakeConnection("127.0.0.1", 1883; client_id="mqtt_client_1")
future = connect_async(client, connection)
wait(future)
```

# 参照

  * [`connect`](@ref): この関数の同期バージョン。
