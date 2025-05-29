```
t8_shmem_array_index(array, index)
```

[`t8_shmem_array`](@ref) の要素への読み取り専用ポインタを返します。

!!! note
    値を変更してはいけません。


!!! note
    *array* の書き込みモードは無効にする必要があります。


# 引数

  * `array`:[in] [`t8_shmem_array`](@ref)。
  * `index`:[in] 要素のインデックス。

# 戻り値

*array* の *index* にある要素へのポインタ。

### プロトタイプ

```c
const void * t8_shmem_array_index (t8_shmem_array_t array, size_t index);
```
