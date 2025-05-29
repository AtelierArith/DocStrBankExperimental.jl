```
aws_server_bootstrap_acquire(bootstrap)
```

サーバーブートストラップの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じサーバーブートストラップを返します。

### プロトタイプ

```c
struct aws_server_bootstrap *aws_server_bootstrap_acquire(struct aws_server_bootstrap *bootstrap);
```
