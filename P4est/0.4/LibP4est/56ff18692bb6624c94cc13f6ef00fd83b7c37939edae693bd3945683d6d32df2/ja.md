```
sc_array_init(array, elem_size)
```

既に割り当てられた（または静的な）配列構造を初期化します。

### パラメータ

  * `array`:[in,out] 初期化される配列構造。
  * `elem_size`:[in] バイト単位の配列要素のサイズ。

### プロトタイプ

```c
void sc_array_init (sc_array_t * array, size_t elem_size);
```
