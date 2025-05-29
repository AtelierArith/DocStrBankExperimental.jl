```
t8_shmem_array_copy(dest, source)
```

1つのt8_shmem配列の内容を別の配列にコピーします。

!!! note
    *dest*は初期化されており、*source*と要素サイズおよび要素数が一致している必要があります。


!!! note
    *dest*は書き込みモードが無効になっている必要があります。


# 引数

  * `dest`:[in,out] *source*がコピーされる配列。
  * `source`:[in] コピーする配列。

### プロトタイプ

```c
void t8_shmem_array_copy (t8_shmem_array_t dest, t8_shmem_array_t source);
```
