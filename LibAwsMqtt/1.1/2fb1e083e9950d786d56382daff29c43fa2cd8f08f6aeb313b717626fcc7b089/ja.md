```
aws_mqtt5_client_acquire(client)
```

mqtt5クライアントへの参照を取得します

# 引数

  * `client`: 参照を取得するクライアント。NULLの可能性があります。

# 戻り値

クライアントとして渡されたもの（クライアントまたはNULL）

### プロトタイプ

```c
struct aws_mqtt5_client *aws_mqtt5_client_acquire(struct aws_mqtt5_client *client);
```
