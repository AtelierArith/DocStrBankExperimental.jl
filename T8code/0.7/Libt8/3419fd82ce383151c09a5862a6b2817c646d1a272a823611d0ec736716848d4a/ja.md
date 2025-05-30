```
t8_forest_get_tree_vertices(forest, ltreeid)
```

木の頂点座標へのポインタを返します。

# 引数

  * `forest`:[in] 森。
  * `ltreeid`:[in] ローカルツリーのID。

# 戻り値

保存されている場合、*tree*の頂点座標へのポインタ。 このツリーの座標が見つからない場合は、NULL。

### プロトタイプ

```c
double * t8_forest_get_tree_vertices (t8_forest_t forest, t8_locidx_t ltreeid);
```
