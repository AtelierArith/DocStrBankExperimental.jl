```
sc_array_new(elem_size)
```

0要素の新しい配列構造を作成します。

### パラメータ

  * `elem_size`:[in] 配列の1要素のサイズ（バイト単位）。

### 戻り値

長さ0の割り当てられた配列を返します。

### プロトタイプ

```c
sc_array_t *sc_array_new (size_t elem_size);
```
