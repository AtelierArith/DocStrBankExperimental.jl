```
p8est_mesh_get_neighbors(p4est_, ghost, mesh, curr_quad_id, direction, neighboring_quads, neighboring_encs, neighboring_qids)
```

特定の方向における区画の隣接四角形を検索します

### パラメータ

  * `p4est`:[in] 操作対象のフォレスト。
  * `ghost`:[in] ゴースト区画。
  * `mesh`:[in] メッシュ構造。
  * `curr_quad_id`:[in] 現在の区画のプロセスローカルID。
  * `direction`:[in] 隣接区画を探す方向は次のようにエンコードされています: 0 .. 5 隣接(-s) across f*i, 6 .. 17 隣接(-s) across e*{i-6} 18 .. 25 隣接(-s) across c_{i-18}
  * `neighboring_quads`:[out] 隣接四角形を含む配列(-s) 空である必要があります、[`p4est_quadrant_t`](@ref)*を含みます。NULLでも構いません、その場合 neighboring_qids は NULL であってはなりません。
  * `neighboring_encs`:[out] 以下に説明する隣接四角形のエンコーディングを含む配列(-s) 空である必要があります、intを含みます。注意: エンコーディングはメッシュに保存されているエンコーディングとは異なることに注意してください。正の値はローカル区画用、負の値はゴースト区画を示します。面: 1 .. 24 => 同サイズの隣接(r * 6 + nf) + 1; nf = 0 .. 5 面インデックス; r = 0 .. 3 相対的な向き 25 .. 120 => 二倍サイズの隣接 25 + h * 24 + r * 6 + nf; h = 0 .. 3 サブ面の番号; r, nf は上記の通り 121 .. 144 => 半サイズの隣接 121 + r * 6 + nf; r, nf は上記の通り エッジ: 1 .. 24 => 同サイズの隣接 r * 12 + ne + 1; ne = 0 .. 11 エッジインデックス; r = 0 .. 1 相対的な向き 25 .. 72 => 二倍サイズの隣接 25 + h * 24 + r * 12 + ne; h = 0 .. 1 サブエッジの番号; r, ne は上記の通り 73 .. 96 => 半サイズの隣接 73 + r * 12 + ne; r, ne は上記の通り コーナー: 1 .. 8 => nc + 1; nc = 0 .. 7 コーナーインデックス
  * `neighboring_qids`:[out] 隣接区画のIDを含む配列。NULLでも構いません、その場合隣接qidsは収集されません。非NULLの場合、配列は空である必要があり、intを含みます。

### プロトタイプ

```c
p4est_locidx_t p8est_mesh_get_neighbors (p8est_t * p4est, p8est_ghost_t * ghost, p8est_mesh_t * mesh, p4est_locidx_t curr_quad_id, p4est_locidx_t direction, sc_array_t * neighboring_quads, sc_array_t * neighboring_encs, sc_array_t * neighboring_qids);
```
