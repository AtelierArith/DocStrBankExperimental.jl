```
t8_shmem_array_get_gloidx_array_for_writing(array)
```

共有メモリ配列のデータへのポインタを、[`t8_gloidx_t`](@ref) 配列として解釈して返します。配列は書き込みが有効でなければならず、t8*shmem*array*end*writing が呼ばれた後にメモリに書き込んではいけません。

# 引数

  * `array`:[in] [`t8_shmem_array`](@ref)

# 戻り値

*array* のデータを [`t8_gloidx_t`](@ref) ポインタとして返します。

### プロトタイプ

```c
t8_gloidx_t * t8_shmem_array_get_gloidx_array_for_writing (t8_shmem_array_t array);
```
