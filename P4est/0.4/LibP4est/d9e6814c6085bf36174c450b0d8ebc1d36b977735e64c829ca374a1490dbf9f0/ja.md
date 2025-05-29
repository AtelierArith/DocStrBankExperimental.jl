```
sc_mempool_memory_used(mempool)
```

メモリプールによって使用されるメモリを計算します。

### パラメータ

  * `array`:[in] メモリプール。

### 戻り値

バイト単位での使用メモリ。

### プロトタイプ

```c
size_t sc_mempool_memory_used (sc_mempool_t * mempool);
```
