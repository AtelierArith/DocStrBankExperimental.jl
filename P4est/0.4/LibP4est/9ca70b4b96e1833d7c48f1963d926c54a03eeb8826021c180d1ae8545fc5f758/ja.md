```
sc_array_init_size(array, elem_size, elem_count)
```

既に割り当てられた（または静的な）配列構造を初期化し、指定された数の要素を割り当てます。非推奨: sc*array*init_countを使用してください。

### パラメータ

  * `array`:[in,out] 初期化される配列構造。
  * `elem_size`:[in] 配列要素1つのサイズ（バイト単位）。
  * `elem_count`:[in] 初期の配列要素の数。

### プロトタイプ

```c
void sc_array_init_size (sc_array_t * array, size_t elem_size, size_t elem_count);
```
