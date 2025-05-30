```
t8_cmesh_tree_vertices_negative_volume(eclass, vertices, num_vertices)
```

与えられたeclassの木のための頂点座標のセットが与えられます。この座標を持つ木の幾何学的体積が負であるかどうかを照会します。

# 引数

  * `eclass`:[in] 木のeclass。
  * `vertices`:[in] 木の頂点の座標。
  * `num_vertices`:[in] 頂点の数。*vertices*は3 * *num_vertices*個の倍精度浮動小数点数を保持する必要があります。*num_vertices*はt8*eclass*num_vertices[*eclass*]と一致しなければなりません。

# 戻り値

*vertices*によって記述される幾何学的体積が負であればTrueを返します。そうでなければFalseを返します。与えられた頂点座標を持つ与えられたeclassの木が負の体積を持つ場合はtrueを返します。

### プロトタイプ

```c
int t8_cmesh_tree_vertices_negative_volume (const t8_eclass_t eclass, const double *vertices, const int num_vertices);
```
