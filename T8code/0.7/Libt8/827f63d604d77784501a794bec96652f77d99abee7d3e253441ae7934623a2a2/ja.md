```
t8_forest_leaf_face_neighbors(forest, ltreeid, leaf, pneighbor_leaves, face, dual_faces, num_neighbors, pelement_indices, pneigh_scheme, forest_is_balanced)
```

森林の葉の面の隣接葉を計算します。

!!! note
    隣接面がない場合、出力時に *neighbor*leaves = NULL, num*neighbors = 0, および *pelement_indices = NULL になります。


!!! note
    現在、*forest* はバランスが取れている必要があります。


!!! note
    この関数を呼び出す前に *forest* をコミットする必要があります。


!!! note
    重要！このルーチンは解放する必要があるメモリを割り当てます。次のように行ってください：


if (num*neighbors > 0) { eclass*scheme->[`t8_element_destroy`](@ref) (num*neighbors, neighbors); [`T8*FREE`](@ref) (pneighbor_leaves); [`T8*FREE`](@ref) (pelement*indices); [`T8_FREE`](@ref) (dual_faces); }

# 引数

  * `forest`:[in] 森。有効なゴーストレイヤーを持っている必要があります。
  * `ltreeid`:[in] ローカルツリーID。
  * `leaf`:[in] *forest* の *ltreeid* のツリー内の葉。
  * `pneighbor_leaves`:[out] 入力時は未割り当て。出力時に隣接葉がここに格納されます。
  * `face`:[in] 隣接面が検索される面のインデックス。
  * `dual_faces`:[out] 出力時に隣接要素の面のIDが格納されます。
  * `num_neighbors`:[out] 出力時に隣接葉の数。
  * `pelement_indices`:[out] 入力時は未割り当て。出力時に隣接葉の要素インデックスがここに格納されます。ローカル葉の場合は 0, 1, ... num*local*el - 1、ゴーストの場合は num*local*el , ... , num*local*el + num_ghosts - 1。
  * `pneigh_scheme`:[out] 出力時に隣接要素のeclassスキーム。
  * `forest_is_balanced`:[in] *forest* がバランスが取れている場合は真、そうでない場合は偽。

### プロトタイプ

```c
void t8_forest_leaf_face_neighbors (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *leaf, t8_element_t **pneighbor_leaves[], int face, int *dual_faces[], int *num_neighbors, t8_locidx_t **pelement_indices, t8_eclass_scheme_c **pneigh_scheme, int forest_is_balanced);
```
