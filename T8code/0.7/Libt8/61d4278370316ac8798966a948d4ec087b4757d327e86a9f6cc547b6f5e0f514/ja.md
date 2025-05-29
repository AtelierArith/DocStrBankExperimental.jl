```
t8_shmem_array_get_array(array)
```

[`t8_shmem_array`](@ref) のデータ配列へのポインタを返します。

!!! note
    *array* の書き込みモードは無効にする必要があります。


# 引数

  * `array`:[in] [`t8_shmem_array`](@ref)。

# 戻り値

*array* のデータ配列へのポインタ。

### プロトタイプ

```c
const void * t8_shmem_array_get_array (t8_shmem_array_t array);
```
