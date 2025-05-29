```
aws_memory_pool_release(mempool, to_release)
```

メモリプールに空きがあればメモリを解放し、そうでなければ `to_release` を解放します。

### プロトタイプ

```c
void aws_memory_pool_release(struct aws_memory_pool *mempool, void *to_release);
```
