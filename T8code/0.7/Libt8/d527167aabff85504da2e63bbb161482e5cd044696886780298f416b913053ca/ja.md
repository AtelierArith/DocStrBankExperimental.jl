```
t8_shmem_array_start_writing(array)
```

共有メモリ配列の書き込みモードを有効にします。配列に書き込むことが許可されているのは一部のプロセスのみであり、その場合は戻り値がゼロ以外になります。

!!! note
    この関数はMPIの集合的操作です。


# 引数

  * `array`:[in,out] 初期化された配列。特定のプロセスで書き込みが有効になります。

# 戻り値

呼び出しプロセスが配列に書き込むことができる場合は真。

### プロトタイプ

```c
int t8_shmem_array_start_writing (t8_shmem_array_t array);
```
