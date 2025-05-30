```
t8_element_array_reset(element_array)
```

配列のカウントをゼロに設定し、すべての要素を解放します。

!!! note
    [`t8_element_array_init`](@ref)を呼び出し、その後に任意の配列操作を行い、次に[`t8_element_array_reset`](@ref)を呼び出すことはメモリに影響を与えません。


# 引数

  * `element_array`:[in,out] リセットされる配列構造。

### プロトタイプ

```c
void t8_element_array_reset (t8_element_array_t *element_array);
```
