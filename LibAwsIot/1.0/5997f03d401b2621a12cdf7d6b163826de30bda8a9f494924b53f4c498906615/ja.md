```
aws_secure_tunnel_release(secure_tunnel)
```

セキュアトンネルへの参照を解放します。セキュアトンネルの参照カウントがゼロになると、セキュアトンネルは自動的に停止をトリガーし、停止が完了すると、セキュアトンネルは自分自身を削除します。

# 引数

  * `secure_tunnel`: 参照を解放するセキュアトンネル。NULLの可能性があります。

# 戻り値

NULL

### プロトタイプ

```c
struct aws_secure_tunnel *aws_secure_tunnel_release(struct aws_secure_tunnel *secure_tunnel);
```
