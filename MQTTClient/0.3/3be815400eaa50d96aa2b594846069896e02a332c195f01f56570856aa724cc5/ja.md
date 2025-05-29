```
subscribe(client::Client, topic::String, on_msg::Function; qos::UInt8=QOS_0)
```

トピックにサブスクライブします。

# 引数

  * `client::Client`: MQTTクライアント。
  * `topic::String`: サブスクライブするトピック。
  * `on_msg::Function`: トピックでメッセージを受信したときに呼び出す関数。
  * `qos::UInt8`: サブスクリプションに使用するサービス品質レベル。デフォルトは0です。

# 例

```julia
subscribe(client, "my/topic", on_msg)
```
