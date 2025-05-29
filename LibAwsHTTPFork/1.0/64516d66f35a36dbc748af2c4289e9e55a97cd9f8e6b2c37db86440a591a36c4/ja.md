```
aws_http_connection_new_requests_allowed(connection)
```

接続が新しいリクエストを行うことができるかどうかを返します。もし false の場合は、さらなるリクエストを行うために新しい接続を確立する必要があります。

### プロトタイプ

```c
bool aws_http_connection_new_requests_allowed(const struct aws_http_connection *connection);
```
