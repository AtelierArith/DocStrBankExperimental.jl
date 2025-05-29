```
t8_shmem_array_destroy(parray)
```

[`t8_shmem_array`](@ref) に関連するすべてのメモリを解放します。

# 引数

  * `parray`:[in,out] 入力時に有効な [`t8_shmem_array`](@ref) へのポインタ。この配列は解放され、戻り値で *parray* は NULL に設定されます。

### プロトタイプ

```c
void t8_shmem_array_destroy (t8_shmem_array_t *parray);
```
