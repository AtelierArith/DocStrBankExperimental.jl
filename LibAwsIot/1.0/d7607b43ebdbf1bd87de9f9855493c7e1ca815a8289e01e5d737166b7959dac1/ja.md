```
aws_secure_tunnel_new(allocator, options)
```

新しいセキュアトンネルを作成します

# 引数

  * `options`: セキュアトンネルの設定

# 戻り値

新しいセキュアトンネルまたはNULL

### プロトタイプ

```c
struct aws_secure_tunnel *aws_secure_tunnel_new( struct aws_allocator *allocator, const struct aws_secure_tunnel_options *options);
```
