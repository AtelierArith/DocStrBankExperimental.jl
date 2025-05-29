```
aws_mqtt5_client_start(client)
```

非同期的にmqtt5クライアントに、構成されたエンドポイントへの接続を試みるよう通知します。クライアントは、mqtt5クライアント設定の再接続関連パラメータのプロパティを使用して接続を維持しようとします。

# 引数

  * `client`: 開始するmqtt5クライアント

# 戻り値

開始プロセスを開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_mqtt5_client_start(struct aws_mqtt5_client *client);
```
