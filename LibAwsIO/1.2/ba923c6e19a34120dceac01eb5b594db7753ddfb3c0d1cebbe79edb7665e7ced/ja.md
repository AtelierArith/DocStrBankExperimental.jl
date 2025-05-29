```
aws_server_bootstrap_release(bootstrap)
```

サーバーブートストラップの参照カウントを減少させます。参照カウントがゼロになると、ブートストラップは破棄されます。

### プロトタイプ

```c
void aws_server_bootstrap_release(struct aws_server_bootstrap *bootstrap);
```
