```
t8_cmesh_set_tree_vertices(cmesh, gtree_id, vertices, num_vertices)
```

cmesh内の木の頂点座標を設定します。これは現在非効率的であり、各木に対して頂点が重複しています。最終的には、この関数はより効率的なものに置き換えられる予定です。この関数は、t8*cmesh*commitの後に呼び出すことはできません。木のeclassは、この関数を呼び出す前に設定する必要があります。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `gtree_id`:[in] 木のグローバル番号。
  * `vertices`:[in] 各木の頂点ごとの3つのダブルの配列。
  * `num_vertices`:[in] *vertices*内の頂点の数。木のコーナーの数と一致する必要があります。

### プロトタイプ

```c
void t8_cmesh_set_tree_vertices (t8_cmesh_t cmesh, const t8_gloidx_t gtree_id, const double *vertices, const int num_vertices);
```
