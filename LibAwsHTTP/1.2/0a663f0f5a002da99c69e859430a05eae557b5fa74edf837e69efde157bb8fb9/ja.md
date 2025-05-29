```
aws_http_connection_release(connection)
```

ユーザーは、接続が完了したらそれを解放する必要があります。この操作が行われるまで、接続のメモリは回収されません。接続がすでにシャットダウンしていない場合は、シャットダウンされます。

ユーザーは、http*connectionに渡されたデータを解放する前に、常にon*shutdown()コールバックが呼び出されるのを待つべきです（例：`aws_tls_connection_options`、`aws_socket_options`）。そうしないと、http_connectionのシャットダウンタスクとメモリ解放タスクの間でレースコンディションが発生し、セグメンテーションフォルトを引き起こす可能性があります。

### プロトタイプ

```c
void aws_http_connection_release(struct aws_http_connection *connection);
```
