```
t8_element_array_resize(element_array, new_count)
```

要素配列に格納されている要素の数を変更します。

!!! note
    *new_count* が *element_array* の現在の要素数より大きい場合、新しい要素に対して t8*element*init が呼び出されます。


# 引数

  * `element_array`:[in,out] 修正される要素配列。
  * `new_count`:[in] 配列の新しい要素数。ゼロの場合、効果は t8*element*array_reset と同じです。

### プロトタイプ

```c
void t8_element_array_resize (t8_element_array_t *element_array, size_t new_count);
```
