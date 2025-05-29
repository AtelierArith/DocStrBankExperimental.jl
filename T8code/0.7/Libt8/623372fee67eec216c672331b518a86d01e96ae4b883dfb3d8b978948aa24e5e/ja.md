```
t8_element_array_get_array_mutable(element_array)
```

t8*element*arrayに格納されている[`sc_array`](@ref)へのミュータブルポインタを返します。

!!! note
    データは変更可能です。


# 引数

  * `element_array`:[in] 配列構造体。

# 戻り値

データを格納している[`sc_array`](@ref)へのポインタ。

### プロトタイプ

```c
sc_array_t * t8_element_array_get_array_mutable (t8_element_array_t *element_array);
```
