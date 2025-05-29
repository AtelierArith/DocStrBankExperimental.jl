```
設定
```

mqttクライアントとmqtt接続データのコンテナです。これは部分的に反復可能で、`...`スプラット演算子または`client, conn = conf`変数代入を使用して2つの変数に展開できます。

## 例

```julia
# MakeConnectionインターフェース関数を使用
config = MakeConnection("/temp/mqtt.sock")

# 定義されたIOを使用
io = IOConnection("localhost", 1883)
config = Configuration(io)

# 変数を展開
client, connection = Configuration(...)
```
