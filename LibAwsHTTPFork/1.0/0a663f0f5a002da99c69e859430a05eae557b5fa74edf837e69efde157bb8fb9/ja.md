```
aws_http_connection_release(connection)
```

ユーザーは、接続が完了したらそれを解放する必要があります。この操作が行われるまで、接続のメモリは回収されません。接続がすでにシャットダウンしていなかった場合、それはシャットダウンされます。

ユーザーは、http*connectionに渡されたデータ（例：`aws*tls*connection*options`、`aws*socket*options`）を解放する前に、常にon*shutdown()コールバックが呼び出されるのを待つべきです。そうしないと、http*connectionのシャットダウンタスクとメモリ解放タスクの間でレースコンディションが発生し、セグメンテーションフォルトを引き起こす可能性があります。

### プロトタイプ

```c
void aws_http_connection_release(struct aws_http_connection *connection);
```
