```
t8_shmem_array_end_writing(array)
```

共有メモリ配列の書き込みモードを無効にします。

!!! note
    この関数はMPIの集合的な操作です。


# 引数

  * `array`:[in,out] 書き込みモードが有効な状態で初期化されています。

# 参照

[`t8_shmem_array_start_writing`](@ref).

### プロトタイプ

```c
void t8_shmem_array_end_writing (t8_shmem_array_t array);
```
