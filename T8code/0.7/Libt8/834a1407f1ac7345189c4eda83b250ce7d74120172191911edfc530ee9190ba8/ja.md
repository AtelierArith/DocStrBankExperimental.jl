```
t8_element_array_init_copy(element_array, scheme, data, num_elements)
```

既に割り当てられた（または静的な）配列構造を初期化し、既存の配列[`t8_element_t`](@ref)をそれにコピーします。

# 引数

  * `element_array`:[in,out] 初期化される配列構造。
  * `scheme`:[in] 要素が格納されるべきeclassスキーム。
  * `data`:[in] *element_array*にコピーされる[`t8_element_t`](@ref)の配列。*data*内の要素は*scheme*に属し、t8*element*newまたはt8*element*initで適切に初期化されている必要があります。
  * `num_elements`:[in] *data*内でコピーされる要素の数。

### プロトタイプ

```c
void t8_element_array_init_copy (t8_element_array_t *element_array, t8_eclass_scheme_c *scheme, t8_element_t *data, size_t num_elements);
```
