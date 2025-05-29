```
subscribe_async(client::Client, topic::String, on_msg::Function; qos::UInt8=QOS_0)
```

トピックに非同期でサブスクライブします。

# 引数

  * `client::Client`: MQTTクライアント。
  * `topic::String`: サブスクライブするトピック。
  * `on_msg::Function`: トピックでメッセージを受信したときに呼び出される関数。
  * `qos::UInt8`: サブスクリプションに使用するサービス品質レベル。デフォルトは0。

# 戻り値

  * `Future`: サブスクリプションの完了を待つために使用できる未来。

# 例

```julia
future = subscribe_async(client, "my/topic", on_msg; qos=QOS_2)
```
