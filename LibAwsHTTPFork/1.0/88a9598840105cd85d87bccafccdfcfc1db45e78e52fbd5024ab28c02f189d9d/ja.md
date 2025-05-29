```
aws_http_connection_is_open(connection)
```

接続が閉じられているか、閉じつつある場合を除き、trueを返します。

### プロトタイプ

```c
bool aws_http_connection_is_open(const struct aws_http_connection *connection);
```
