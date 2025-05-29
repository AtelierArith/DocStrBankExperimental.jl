```
t8_cmesh_get_partition_table(cmesh)
```

分割されたcmeshのパーティションテーブルを格納する共有メモリ配列を返します。

# 引数

  * `cmesh`:[in] cmesh。

# 戻り値

パーティション配列。cmeshが分割されていない場合や、パーティション配列が*cmesh*に格納されていない場合はNULL。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_shmem_array_t t8_cmesh_get_partition_table (t8_cmesh_t cmesh);
```
