```
sc_array_new_data(base, elem_size, elem_count)
```

既存のプレーンC配列の新しいビューを作成します。

### パラメータ

  * `base`:[in] ビューが生存している間、データは移動してはいけません。
  * `elem_size`:[in] 配列要素のサイズ（バイト単位）。
  * `elem_count`:[in] ビューの長さ（要素単位）。ビューはこの長さを超えてサイズ変更することはできません。

### プロトタイプ

```c
sc_array_t *sc_array_new_data (void *base, size_t elem_size, size_t elem_count);
```
