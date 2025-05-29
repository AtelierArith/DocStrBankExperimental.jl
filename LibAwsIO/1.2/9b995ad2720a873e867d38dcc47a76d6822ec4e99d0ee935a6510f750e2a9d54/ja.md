```
aws_memory_pool_acquire(mempool)
```

プールからメモリを取得します。利用可能でない場合は、割り当てを試みて結果を返します。

### プロトタイプ

```c
void *aws_memory_pool_acquire(struct aws_memory_pool *mempool);
```
