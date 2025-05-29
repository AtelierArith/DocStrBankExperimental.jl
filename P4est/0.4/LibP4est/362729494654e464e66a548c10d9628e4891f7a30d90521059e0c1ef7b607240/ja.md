```
sc_array_new_count(elem_size, elem_count)
```

指定された長さ（要素数）を持つ新しい配列構造を作成します。

### パラメータ

  * `elem_size`:[in] 1つの配列要素のサイズ（バイト単位）。
  * `elem_count`:[in] 初期の配列要素数。

### 戻り値

割り当てられたが初期化されていない要素を持つ配列を返します。

### プロトタイプ

```c
sc_array_t *sc_array_new_count (size_t elem_size, size_t elem_count);
```
