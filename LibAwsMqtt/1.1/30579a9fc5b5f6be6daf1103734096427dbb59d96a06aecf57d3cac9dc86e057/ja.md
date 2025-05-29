```
aws_mqtt_client_connection_subscribe_multiple(connection, topic_filters, on_suback, on_suback_ud)
```

トピックフィルターにサブスクライブします。各トピックフィルターに一致するPUBLISHが受信されると、on_publishが呼び出されます。

# 引数

  * `connection`:[in] サブスクライブする接続
  * `topic_filters`:[in] リクエストを説明する[`aws_mqtt_topic_subscription`](@ref)のarray_list（ポインタではない）。
  * `on_suback`:[in](nullable) サーバーからSUBACKが受信され、サブスクリプションが完了したときに呼び出されます。ブローカーはトピックの1つを失敗させる可能性があるため、コールバックからの[`aws_mqtt_topic_subscription`](@ref)のqosを確認してください。
  * `on_suback_ud`:[in](nullable) on_subackに渡されます。

# 戻り値

成功裏に送信された場合はサブスクライブパケットのパケットID、そうでない場合は0。

### プロトタイプ

```c
uint16_t aws_mqtt_client_connection_subscribe_multiple( struct aws_mqtt_client_connection *connection, const struct aws_array_list *topic_filters, aws_mqtt_suback_multi_fn *on_suback, void *on_suback_ud);
```
