```
t8_cmesh_get_partition_table(cmesh)
```

分割されたcmeshの分割テーブルを格納している共有メモリ配列を返します。

# 引数

  * `cmesh`:[in] cmesh。

# 戻り値

分割配列。cmeshが分割されていない場合や、分割配列が*cmesh*に格納されていない場合はNULLを返します。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_shmem_array_t t8_cmesh_get_partition_table (t8_cmesh_t cmesh);
```
