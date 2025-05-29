```
t8_shmem_array_get_gloidx(array, index)
```

共有メモリ配列から[`t8_gloidx_t`](@ref)を格納するエントリを返します。

!!! note
    書き込みモードは*array*に対して無効にする必要があります。


# 引数

  * `array`:[in] [`t8_shmem_array`](@ref)
  * `index`:[in] 取得するエントリのインデックス。

# 戻り値

*array*の*index*-番目のエントリを[`t8_gloidx_t`](@ref)として返します。

### プロトタイプ

```c
t8_gloidx_t t8_shmem_array_get_gloidx (t8_shmem_array_t array, int index);
```
