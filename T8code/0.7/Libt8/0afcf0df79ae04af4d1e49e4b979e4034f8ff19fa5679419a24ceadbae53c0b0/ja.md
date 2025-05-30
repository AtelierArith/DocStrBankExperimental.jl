```
t8_forest_leaf_face_neighbors_ext(forest, ltreeid, leaf, pneighbor_leaves, face, dual_faces, num_neighbors, pelement_indices, pneigh_scheme, forest_is_balanced, gneigh_tree, orientation)
```

t8*forest*leaf*face*neighborsと同様ですが、グローバルな隣接情報と向きも提供します。

!!! note
    隣接する面がない場合、*neighbor*leaves = NULL、num*neighbors = 0、および*pelement_indices = NULLが出力されます。


!!! note
    現在、*forest*はバランスが取れている必要があります。


!!! note
    この関数を呼び出す前に*forest*をコミットする必要があります。


!!! note
    重要！このルーチンはメモリを割り当てるため、解放する必要があります。次のように行ってください：


if (num*neighbors > 0) { eclass*scheme->[`t8_element_destroy`](@ref) (num*neighbors, neighbors); [`T8*FREE`](@ref) (pneighbor_leaves); [`T8*FREE`](@ref) (pelement*indices); [`T8_FREE`](@ref) (dual_faces); }

# 引数

  * `forest`:[in] 森。有効なゴーストレイヤーを持っている必要があります。
  * `ltreeid`:[in] ローカルツリーID。
  * `leaf`:[in] *forest*の*ltreeid*のツリー内の葉。
  * `pneighbor_leaves`:[out] 入力時は未割り当て。出力時に隣接する葉がここに格納されます。
  * `face`:[in] 隣接する面が検索される面のインデックス。
  * `dual_faces`:[out] 出力時に隣接する要素の面のIDが格納されます。
  * `num_neighbors`:[out] 出力時に隣接する葉の数。
  * `pelement_indices`:[out] 入力時は未割り当て。出力時に隣接する葉の要素インデックスがここに格納されます。ローカル葉の場合は0, 1, ... num*local*el - 1、ゴーストの場合はnum*local*el, ... , num*local*el + num_ghosts - 1。
  * `pneigh_scheme`:[out] 出力時に隣接する要素のeclassスキーム。
  * `forest_is_balanced`:[in] *forest*がバランスが取れている場合はtrue、そうでない場合はfalse。
  * `gneigh_tree`:[out] 隣接するツリーのグローバルツリーID。
  * `orientation`:[out] 入力時にNULLでない場合、面の向きが計算されてここに格納されます。したがって、面の接続がツリー間接続である場合、ツリー間接続の向きが格納されます。それ以外の場合は、値0が格納されます。他のすべてのパラメータと動作は`t8_forest_leaf_face_neighbors`と同じです。

### プロトタイプ

```c
void t8_forest_leaf_face_neighbors_ext (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *leaf, t8_element_t **pneighbor_leaves[], int face, int *dual_faces[], int *num_neighbors, t8_locidx_t **pelement_indices, t8_eclass_scheme_c **pneigh_scheme, int forest_is_balanced, t8_gloidx_t *gneigh_tree, int *orientation);
```
