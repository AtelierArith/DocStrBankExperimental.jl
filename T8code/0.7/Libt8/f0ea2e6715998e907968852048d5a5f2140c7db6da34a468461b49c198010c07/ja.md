```
t8_element_array_get_data(element_array)
```

t8*element*arrayに格納されている実際のデータ配列への定数ポインタを返します。

# 引数

  * `element_array`:[in] 配列構造体。

# 戻り値

格納されたデータへのポインタ。格納された要素の数が0の場合、NULLが返されます。

### プロトタイプ

```c
const t8_element_t * t8_element_array_get_data (const t8_element_array_t *element_array);
```
