```
aws_mqtt5_client_release(client)
```

mqtt5クライアントへの参照を解放します。クライアントの参照カウントがゼロになると、クライアントは自動的に停止をトリガーし、停止が完了すると、クライアントは自分自身を削除します。

# 引数

  * `client`: 参照を解放するクライアント。NULLである可能性があります。

# 戻り値

NULL

### プロトタイプ

```c
struct aws_mqtt5_client *aws_mqtt5_client_release(struct aws_mqtt5_client *client);
```
