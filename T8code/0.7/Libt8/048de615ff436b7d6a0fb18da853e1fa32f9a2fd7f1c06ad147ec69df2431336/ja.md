```
t8_shmem_array_get_gloidx_array(array)
```

共有メモリ配列のデータを[`t8_gloidx_t`](@ref)配列として解釈した読み取り専用ポインタを返します。

!!! note
    書き込みモードは*array*に対して無効にする必要があります。


# 引数

  * `array`:[in] [`t8_shmem_array`](@ref)

# 戻り値

*array*のデータを[`t8_gloidx_t`](@ref)ポインタとして返します。

### プロトタイプ

```c
const t8_gloidx_t * t8_shmem_array_get_gloidx_array (t8_shmem_array_t array);
```
