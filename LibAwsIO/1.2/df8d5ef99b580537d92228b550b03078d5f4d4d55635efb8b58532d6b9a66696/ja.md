```
aws_client_bootstrap_acquire(bootstrap)
```

クライアントブートストラップの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じクライアントブートストラップを返します。

### プロトタイプ

```c
struct aws_client_bootstrap *aws_client_bootstrap_acquire(struct aws_client_bootstrap *bootstrap);
```
