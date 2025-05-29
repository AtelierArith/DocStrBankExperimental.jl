```
sc_array_init_count(array, elem_size, elem_count)
```

既に割り当てられた（または静的な）配列構造を初期化し、指定された数の要素を割り当てます。この関数は sc*array*init_size を置き換えます。

### パラメータ

  * `array`:[in,out] 初期化される配列構造。
  * `elem_size`:[in] 配列要素1つのサイズ（バイト単位）。
  * `elem_count`:[in] 初期配列要素の数。

### プロトタイプ

```c
void sc_array_init_count (sc_array_t * array, size_t elem_size, size_t elem_count);
```
