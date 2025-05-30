```
t8_element_array_init_size(element_array, scheme, num_elements)
```

既に割り当てられた（または静的な）配列構造を初期化し、指定された数の要素を割り当て、それらをt8*element*initで初期化します。

# 引数

  * `element_array`:[in,out] 初期化される配列構造。
  * `scheme`:[in] 要素が格納されるべきeclassスキーム。
  * `num_elements`:[in] 初期配列要素の数。

### プロトタイプ

```c
void t8_element_array_init_size (t8_element_array_t *element_array, t8_eclass_scheme_c *scheme, size_t num_elements);
```
