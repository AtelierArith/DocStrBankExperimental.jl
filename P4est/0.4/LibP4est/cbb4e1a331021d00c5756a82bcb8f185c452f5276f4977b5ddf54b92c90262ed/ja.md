```
sc_mempool_new(elem_size)
```

ゼロおよび永続オプションがオフの新しいメモリプール構造を作成します。sc*mempool*allocによって返される要素の内容は未定義です。

### パラメータ

  * `elem_size`:[in] バイト単位の1つの要素のサイズ。

### 戻り値

割り当てられ、初期化されたメモリプールを返します。

### プロトタイプ

```c
sc_mempool_t *sc_mempool_new (size_t elem_size);
```
