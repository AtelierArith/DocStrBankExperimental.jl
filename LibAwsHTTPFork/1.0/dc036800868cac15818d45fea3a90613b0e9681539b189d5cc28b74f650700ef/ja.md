```
aws_http_connection_stop_new_requests(connection)
```

接続の新しいリクエストの受け入れを停止します。接続のシャットダウンプロセスは開始されません。すでにオープンしているリクエストは完了を待つことができますが、新しいリクエストは作成に失敗します。

### プロトタイプ

```c
void aws_http_connection_stop_new_requests(struct aws_http_connection *connection);
```
