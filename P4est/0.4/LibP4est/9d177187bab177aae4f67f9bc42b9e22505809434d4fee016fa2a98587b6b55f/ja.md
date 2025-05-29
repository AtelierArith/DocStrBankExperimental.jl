```
sc_mempool_init(mempool, elem_size)
```

[`sc_mempool_new`](@ref) と同様ですが、すでに割り当てられた [`sc_mempool_t`](@ref) ポインタ用です。

### プロトタイプ

```c
void sc_mempool_init (sc_mempool_t * mempool, size_t elem_size);
```
