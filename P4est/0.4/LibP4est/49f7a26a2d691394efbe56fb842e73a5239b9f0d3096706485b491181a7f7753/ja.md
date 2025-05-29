```
sc_mempool_destroy(mempool)
```

メモリプール構造体を破棄します。まだ使用中のすべての要素は無効になります。

### パラメータ

  * `mempool`:[in,out] そのメモリは解放されます。

### プロトタイプ

```c
void sc_mempool_destroy (sc_mempool_t * mempool);
```
