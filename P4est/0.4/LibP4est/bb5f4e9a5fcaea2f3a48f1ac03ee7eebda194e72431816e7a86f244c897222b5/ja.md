```
p4est_get_plex_data_ext(p4est_, ghost, lnodes, ctype, overlap, first_local_quad, out_points_per_dim, out_cone_sizes, out_cones, out_cone_orientations, out_vertex_coords, out_children, out_parents, out_childids, out_leaves, out_remotes, custom_numbering)
```

森林のPETSc DMPLEX表現を作成するために必要なデータを作成し、付随するlnodesとゴーストレイヤーを作成します。森林は少なくとも面バランスでなければなりません（[`p4est_balance`](@ref)()を参照）。使用例についてはtest/test_plex2.cを参照してください。

すべての配列は、[`p4est_locidx_t`](@ref)のサイズを保持するように初期化する必要があります。ただし、*out_remotes*は（2 * sizeof ([`p4est_locidx_t`](@ref)））を保持するように初期化する必要があります。

### パラメータ

  * `p4est`:[in] 森
  * `ghost`:[out] ゴーストレイヤー
  * `lnodes`:[out] lnodes
  * `ctype`:[in] オーバーラップの隣接タイプ
  * `overlap`:[in] オーバーラップの層の数（ゼロは許可される）
  * `first_local_quad`:[out] ローカル四分木は、このインデックスから始まる連続したplexインデックスが割り当てられる
  * `out_points_per_dim`:[in,out] DMPlexCreateFromDAG()の引数で埋められる
  * `out_cone_sizes`:[in,out] DMPlexCreateFromDAG()の引数で埋められる
  * `out_cones`:[in,out] DMPlexCreateFromDAG()の引数で埋められる
  * `out_cone_orientations`:[in,out] DMPlexCreateFromDAG()の引数で埋められる
  * `out_vertex_coords`:[in,out] DMPlexCreateFromDAG()の引数で埋められる
  * `out_children`:[in,out] DMPlexSetTree()の引数で埋められる
  * `out_parents`:[in,out] DMPlexSetTree()の引数で埋められる
  * `out_childids`:[in,out] DMPlexSetTree()の引数で埋められる
  * `out_leaves`:[in,out] PetscSFSetGraph()の引数で埋められる
  * `out_remotes`:[in,out] PetscSFSetGraph()の引数で埋められる
  * `custom_numbering`:[in] DMPlex子IDのデフォルト番号付け（0）を使用するか、カスタム（1）を使用するか。

### プロトタイプ

```c
void p4est_get_plex_data_ext (p4est_t * p4est, p4est_ghost_t ** ghost, p4est_lnodes_t ** lnodes, p4est_connect_type_t ctype, int overlap, p4est_locidx_t * first_local_quad, sc_array_t * out_points_per_dim, sc_array_t * out_cone_sizes, sc_array_t * out_cones, sc_array_t * out_cone_orientations, sc_array_t * out_vertex_coords, sc_array_t * out_children, sc_array_t * out_parents, sc_array_t * out_childids, sc_array_t * out_leaves, sc_array_t * out_remotes, int custom_numbering);
```
