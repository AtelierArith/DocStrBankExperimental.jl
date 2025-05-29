```
T8codeMesh(ndims, ntrees, nelements, tree_node_coordinates, nodes,
           boundary_names, treeIDs, neighIDs, faces, duals,
           orientations, levels, num_elements_per_tree)
```

`T8codeMesh`のコンストラクタ。通常は`load_mesh`ルーチンによって呼び出されます。

# 引数

  * `ndims`: メッシュの次元。
  * `ntrees`: グローバルな木の数。
  * `nelements`: グローバルな要素の数。
  * `tree_node_coordinates`: 各木のノード座標: [次元, i, j, k, 木]
  * `nodes`: 補間ノードの配列。
  * `boundary_names`: 境界名のリスト。
  * `treeIDs`: 木のIDのリスト。長さは粗いメッシュの適合インターフェースの数です。
  * `neighIDs`: 隣接する木のIDのリスト。`treeIDs`と同じ長さです。
  * `faces`: 面のIDのリスト。`treeIDs`と同じ長さです。
  * `duals`: 隣接する木の面のIDのリスト。`treeIDs`と同じ長さです。
  * `orientations`: インターフェースの向き番号。`treeIDs`と同じ長さです。
  * `levels`: 各要素のレベルのリスト。長さは`nelements`です。
  * `num_elements_per_tree`: 各木のグローバルな要素数のリスト。長さは`ntrees`です。

入力引数によって再構築された森林を持つ`T8codeMesh`オブジェクトを返します。
