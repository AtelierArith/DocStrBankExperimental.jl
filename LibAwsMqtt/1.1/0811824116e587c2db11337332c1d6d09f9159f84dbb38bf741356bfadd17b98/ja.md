```
aws_mqtt_resubscribe_existing_topics(connection, on_suback, on_suback_ud)
```

現在購読しているすべてのトピックに再購読します。これは、クリーンセッションで接続を再開する際に役立ちます。

# 引数

  * `connection`:[in] 購読する接続
  * `on_suback`:[in](nullable) サーバーからSUBACKが受信され、購読が完了したときに呼び出される
  * `on_suback_ud`:[in](nullable) on_subackに渡される

# 戻り値

購読パケットが正常に送信された場合は購読パケットのIDを返し、そうでない場合は0を返します（その場合、aws*last*error()が設定されます）。

### プロトタイプ

```c
uint16_t aws_mqtt_resubscribe_existing_topics( struct aws_mqtt_client_connection *connection, aws_mqtt_suback_multi_fn *on_suback, void *on_suback_ud);
```
