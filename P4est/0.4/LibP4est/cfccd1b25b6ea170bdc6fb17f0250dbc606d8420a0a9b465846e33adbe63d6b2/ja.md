```
sc_mstamp_memory_used(mst)
```

コンテナ内に割り当てられたすべてのデータのメモリサイズをバイト単位で返します。

### パラメータ

  * `Properly`:[in] 初期化されたスタンプコンテナ。

### 戻り値

コンテナの総メモリサイズ（バイト単位）。

### プロトタイプ

```c
size_t sc_mstamp_memory_used (sc_mstamp_t * mst);
```
