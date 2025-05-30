```
t8_element_array_truncate(element_array)
```

配列のカウントをゼロに設定しますが、要素は解放しません。

!!! note
    これは、t8*element*arrayを再利用可能なバッファとして使用できるようにすることを意図しており、バッファの「高水準マーク」が保持されるため、バッファの寿命にわたってO(log (max n))の再割り当てが発生します。


# 引数

  * `element_array`:[in,out] 切り捨てる要素配列構造体。

### プロトタイプ

```c
void t8_element_array_truncate (t8_element_array_t *element_array);
```
