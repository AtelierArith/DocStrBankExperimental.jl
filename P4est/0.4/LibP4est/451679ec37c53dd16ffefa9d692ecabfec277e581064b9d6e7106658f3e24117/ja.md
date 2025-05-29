```
sc_mempool_destroy_null(pmempool)
```

メモリプール構造体を破棄します。まだ使用中のすべての要素は無効になります。

### パラメータ

  * `pmempool`:[in,out] メモリプールへのポインタのアドレス。そのメモリは解放され、ポインタはNULLに設定されます。

### プロトタイプ

```c
void sc_mempool_destroy_null (sc_mempool_t ** pmempool);
```
