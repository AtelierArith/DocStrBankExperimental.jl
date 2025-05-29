[Mosquitto.jl](https://github.com/denglerchr/Mosquitto.jl) クライアントのためのプロトコル、Mango エージェント用。

# 作成

```
MQTTProtocol(client_id::String, broker_addr::InetAddr)
```

`broker_addr` にあるブローカーに `client_id` で接続する MQTT クライアントを作成します。

# フィールド

  * client - Mosquitto.jl クライアント
  * broker_addr - 接続する MQTT ブローカーのアドレス
  * connected - 接続状態を示す内部フラグ
  * active - リスンループのアクティビティを示す内部フラグ
  * msg_channel - MQTT クライアントのメッセージチャネル
  * conn_channel - MQTT クライアントの接続チャネル
  * topic*to*aid - どの登録エージェントがどのトピックにサブスクライブしているかを追跡する内部辞書
