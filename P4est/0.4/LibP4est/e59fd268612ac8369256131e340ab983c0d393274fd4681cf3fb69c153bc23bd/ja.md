```
sc_mempool_new_zero_and_persist(elem_size)
```

ゼロおよび永続オプションがオンの新しいメモリプール構造を作成します。新しく作成された要素のメモリはゼロに設定され、要素の内容は解放と再返却の間に変更されません。

### パラメータ

  * `elem_size`:[in] 1つの要素のサイズ（バイト単位）。

### 戻り値

割り当てられ、初期化されたメモリプールを返します。

### プロトタイプ

```c
sc_mempool_t *sc_mempool_new_zero_and_persist (size_t elem_size);
```
