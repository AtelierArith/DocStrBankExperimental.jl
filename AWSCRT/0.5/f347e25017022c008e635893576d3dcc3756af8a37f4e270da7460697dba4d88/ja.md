```
ShadowClient(
    connection::MQTTConnection,
)
```

デバイスシャドウサービスクライアント。 [AWS Documentation](https://docs.aws.amazon.com/iot/latest/developerguide/iot-device-shadows.html)。

引数:

  * `connection (MQTTConnection)`: 公開および購読するためのMQTT接続。
  * `thing_name (String)`: シャドウドキュメントが存在するAWS IoT内のThingの名前。
  * `shadow_name (Union{String,Nothing})`: 名前付きシャドウドキュメントのためのシャドウ名、または名前のないシャドウドキュメントのための`nothing`。
