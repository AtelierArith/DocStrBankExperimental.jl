```
t8_element_array_push_count(element_array, count)
```

配列を指定された数の要素で拡張します。

# 引数

  * `element_array`:[in] 修正される配列構造。
  * `count`:[in] 追加する要素の数。

# 戻り値

t8*element*initが呼び出された新しく追加された要素へのポインタを返します。

### プロトタイプ

```c
t8_element_t * t8_element_array_push_count (t8_element_array_t *element_array, size_t count);
```
