```
t8_shmem_array_set_gloidx(array, index, value)
```

[`t8_gloidx_t`](@ref)を格納するために使用されるt8_shmem配列のエントリを設定します。配列は書き込みモードが有効である必要があります t8*shmem*array*start*writing。

# 引数

  * `array`:[in,out] 修正される配列。
  * `index`:[in] 修正される配列エントリ。
  * `value`:[in] 設定される新しい値。

### プロトタイプ

```c
void t8_shmem_array_set_gloidx (t8_shmem_array_t array, int index, t8_gloidx_t value);
```
