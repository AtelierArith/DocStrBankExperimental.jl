```
aws_mqtt5_client_acquire(client)
```

mqtt5 クライアントへの参照を取得します

# 引数

  * `client`: 参照を取得するクライアント。NULL の場合があります。

# 戻り値

渡されたクライアント（クライアントまたは NULL）

### プロトタイプ

```c
struct aws_mqtt5_client *aws_mqtt5_client_acquire(struct aws_mqtt5_client *client);
```
