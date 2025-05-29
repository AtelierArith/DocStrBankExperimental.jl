```
aws_host_resolver_acquire(resolver)
```

ホストリゾルバの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じホストリゾルバを返します。

### プロトタイプ

```c
struct aws_host_resolver *aws_host_resolver_acquire(struct aws_host_resolver *resolver);
```
