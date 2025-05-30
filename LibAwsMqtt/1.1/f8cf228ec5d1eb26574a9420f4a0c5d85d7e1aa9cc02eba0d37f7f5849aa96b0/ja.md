```
aws_mqtt5_client_subscribe(client, subscribe_options, completion_options)
```

mqtt5クライアントでSubscribe操作をキューに追加します

# 引数

  * `client`: Subscribeをキューに追加するmqtt5クライアント
  * `subscribe_options`: Subscribe操作のための設定オプション
  * `completion_options`: 完了コールバックの設定。対応するSUBACKが受信されるか、失敗条件に達したときに呼び出されます。エラーコードはSubscribeの完全な失敗を示し、成功コードはユーザーがすべてのSUBACKの理由コードをチェックして、各サブスクリプションのフィードバックを確認する必要があることを示します。

# 戻り値

Subscribe操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_mqtt5_client_subscribe( struct aws_mqtt5_client *client, const struct aws_mqtt5_packet_subscribe_view *subscribe_options, const struct aws_mqtt5_subscribe_completion_options *completion_options);
```
