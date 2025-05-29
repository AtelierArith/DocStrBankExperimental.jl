```
t8_shmem_array_index_for_writing(array, index)
```

書き込みモードの[`t8_shmem_array`](@ref)内の要素へのポインタを返します。

!!! note
    次のt8*shmem*array*end*writingの呼び出しの前に値を変更できます。


!!! note
    *array*の書き込みモードを有効にする必要があります。


# 引数

  * `array`:[in] [`t8_shmem_array`](@ref)。
  * `index`:[in] 要素のインデックス。

# 戻り値

*array*内の*index*の要素へのポインタ。

### プロトタイプ

```c
void * t8_shmem_array_index_for_writing (t8_shmem_array_t array, size_t index);
```
