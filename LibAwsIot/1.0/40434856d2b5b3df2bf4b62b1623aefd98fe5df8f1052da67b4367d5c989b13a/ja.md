```
aws_secure_tunnel_acquire(secure_tunnel)
```

セキュアトンネルへの参照を取得します

# 引数

  * `secure_tunnel`: 参照を取得するセキュアトンネル。NULLの可能性があります

# 戻り値

渡されたセキュアトンネル（クライアントまたはNULL）

### プロトタイプ

```c
struct aws_secure_tunnel *aws_secure_tunnel_acquire(struct aws_secure_tunnel *secure_tunnel);
```
