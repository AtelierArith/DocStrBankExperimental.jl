```
t8_element_array_get_array(element_array)
```

t8*element*arrayに格納されている[`sc_array`](@ref)へのconstポインタを返します。

!!! note
    データは変更できません。


# 引数

  * `element_array`:[in] 配列構造体。

# 戻り値

データを格納している[`sc_array`](@ref)へのconstポインタ。

### プロトタイプ

```c
const sc_array_t * t8_element_array_get_array (const t8_element_array_t *element_array);
```
