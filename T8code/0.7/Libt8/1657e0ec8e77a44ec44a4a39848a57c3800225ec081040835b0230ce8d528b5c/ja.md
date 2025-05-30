```
t8_cmesh_get_tree_vertices(cmesh, ltreeid)
```

木の頂点座標へのポインタを返します。

# 引数

  * `cmesh`:[in] cmesh。
  * `ltreeid`:[in] ローカルツリーのID。

# 戻り値

保存されている場合、*tree*の頂点座標へのポインタ。 このツリーの座標が見つからない場合は、NULL。

### プロトタイプ

```c
double * t8_cmesh_get_tree_vertices (t8_cmesh_t cmesh, t8_locidx_t ltreeid);
```
