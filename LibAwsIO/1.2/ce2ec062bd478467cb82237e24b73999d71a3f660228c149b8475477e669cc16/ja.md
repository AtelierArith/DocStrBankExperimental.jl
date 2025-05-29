```
aws_client_bootstrap_release(bootstrap)
```

クライアントブートストラップの参照カウントを減少させます。参照カウントがゼロになると、ブートストラップは破棄されます。

### プロトタイプ

```c
void aws_client_bootstrap_release(struct aws_client_bootstrap *bootstrap);
```
