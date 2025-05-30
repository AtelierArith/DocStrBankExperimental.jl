```
aws_mqtt5_client_unsubscribe(client, unsubscribe_options, completion_options)
```

mqtt5 クライアントでの Unsubscribe 操作をキューに追加します

# 引数

  * `client`: Unsubscribe のキューを追加する mqtt5 クライアント
  * `unsubscribe_options`: Unsubscribe 操作のための設定オプション
  * `completion_options`: 完了コールバックの設定。対応する UNSUBACK が受信されるか、失敗条件に達したときに呼び出されます。エラーコードは Unsubscribe の完全な失敗を示し、成功コードはユーザーがすべての UNSUBACK の理由コードをトピックフィルターごとに確認する必要があることを示します。

# 戻り値

Unsubscribe 操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_mqtt5_client_unsubscribe( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_unsubscribe_view *unsubscribe_options, const struct aws_mqtt5_unsubscribe_completion_options *completion_options);
```
