```
aws_mqtt_client_connection_use_websockets(connection, transformer, transformer_ud, validator, validator_ud)
```

接続時にウェブソケットを介したMQTTを使用します。MQTT*WITH*WEBSOCKETSビルドオプションが必要です。

このシナリオでは、HTTP接続が確立され、その後ウェブソケット接続にアップグレードされ、MQTTデータを送信するために使用されます。

# 引数

  * `connection`:[in] 接続オブジェクト。
  * `transformer`:[in] [optional] ウェブソケットハンドシェイクリクエストを変換する可能性のある関数。詳細については[`aws_mqtt_transform_websocket_handshake_fn`](@ref)を参照してください。
  * `transformer_ud`:[in] [optional] request_transformerのユーザーデータ。
  * `validator`:[in] [optional] ウェブソケットハンドシェイクレスポンスを拒否する可能性のある関数。
  * `validator_ud`:[in] [optional] response_validatorのユーザーデータ。

### プロトタイプ

```c
int aws_mqtt_client_connection_use_websockets( struct aws_mqtt_client_connection *connection, aws_mqtt_transform_websocket_handshake_fn *transformer, void *transformer_ud, aws_mqtt_validate_websocket_handshake_fn *validator, void *validator_ud);
```
