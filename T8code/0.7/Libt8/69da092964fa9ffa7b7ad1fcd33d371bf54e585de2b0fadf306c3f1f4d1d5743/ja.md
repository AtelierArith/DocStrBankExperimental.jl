```
t8_element_array_index_int_mutable(element_array, index)
```

配列内の指定された要素を返します。可変バージョン。

# 引数

  * `element_array`:[in] 要素の配列。
  * `index`:[in] 配列内の要素のインデックス。

# 戻り値

*element_array*の*index*位置に格納されている要素へのポインタ。

### プロトタイプ

```c
t8_element_t * t8_element_array_index_int_mutable (t8_element_array_t *element_array, int index);
```
