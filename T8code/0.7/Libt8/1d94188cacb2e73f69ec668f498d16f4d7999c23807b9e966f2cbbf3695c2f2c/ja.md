```
t8_element_array_new_count(scheme, num_elements)
```

指定された長さ（要素数）で新しい配列構造を作成し、それらの要素に対してt8*element*newを呼び出します。

# 引数

  * `scheme`:[in] 要素が格納されるべきeclassスキーム。
  * `num_elements`:[in] 配列要素の初期数。

# 戻り値

t8*element*newが呼び出された要素のために割り当てられ、初期化された要素を持つ割り当てられた配列を返します。

### プロトタイプ

```c
t8_element_array_t * t8_element_array_new_count (t8_eclass_scheme_c *scheme, size_t num_elements);
```
