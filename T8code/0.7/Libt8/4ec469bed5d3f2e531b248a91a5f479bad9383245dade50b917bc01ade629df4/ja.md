```
t8_element_array_get_size(element_array)
```

[`t8_element_array_t`](@ref) に格納されている要素のデータサイズを返します。

# 引数

  * `element_array`:[in] 配列構造体。

# 戻り値

*element_array* の単一要素のサイズ（バイト単位）。

### プロトタイプ

```c
size_t t8_element_array_get_size (const t8_element_array_t *element_array);
```
