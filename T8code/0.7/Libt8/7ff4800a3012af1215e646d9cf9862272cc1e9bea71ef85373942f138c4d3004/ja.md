```
t8_cmesh_set_partition_offsets(cmesh, tree_offsets)
```

cmeshが分割されたcmeshとして理解され、各プロセスの最初のローカルツリーを指定します。この呼び出しは、cmeshがまだt8*cmesh*commitへの呼び出しを介してコミットされていない場合にのみ有効です。代わりにt8*cmesh*set*partition*rangeが呼び出され、cmeshが派生している場合、オフセット配列はコミット中に構築されます。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `tree_offsets`:[in] 各プロセスのためのグローバルtree_idオフセットの配列をここで指定できます。TODO: 共有ツリーのフラグを文書化する。

### プロトタイプ

```c
void t8_cmesh_set_partition_offsets (t8_cmesh_t cmesh, t8_shmem_array_t tree_offsets);
```
