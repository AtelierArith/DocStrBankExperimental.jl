```
t8_cmesh_trees_copy_toproc(trees_dest, trees_src, lnum_trees, lnum_ghosts)
```

1つのツリー構造から別のツリー構造にtree*to*procおよびghost*to*proc配列をコピーします。

# 引数

  * `trees_dest`:[in,out] 目的のツリー構造。
  * `trees_src`:[in] ソースのツリー構造。
  * `lnum_trees`:[in] *trees_src* に格納されているツリーの総数。
  * `lnum_ghosts`:[in] *trees_src* に格納されているゴーストの総数。

### プロトタイプ

```c
void t8_cmesh_trees_copy_toproc (t8_cmesh_trees_t trees_dest, t8_cmesh_trees_t trees_src, t8_locidx_t lnum_trees, t8_locidx_t lnum_ghosts);
```
