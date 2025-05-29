```
p4est_mesh_get_neighbors(p4est_, ghost, mesh, curr_quad_id, direction, neighboring_quads, neighboring_encs, neighboring_qids)
```

特定の方向における区画の隣接四角形を検索します。

### パラメータ

  * `p4est`:[in] 作業対象のフォレスト。
  * `ghost`:[in] ゴーストレイヤー。
  * `mesh`:[in] メッシュ構造。
  * `curr_quad_id`:[in] 現在の四角形のプロセスローカルID。
  * `direction`:[in] 隣接する四角形を探す方向iは次のようにエンコードされます: 0 .. 3 は面iを越えた隣接者、4 .. 7 はコーナーi-4を越えた隣接者。TODO: 空の出力配列の任意の組み合わせを許可する。
  * `neighboring_quads`:[out] 隣接四角形を含む配列。入力時には空である必要があり、[`p4est_quadrant_t`](@ref) *のサイズでなければなりません。NULLでも構いませんが、その場合は**neighboring_qids**はNULLであってはなりません。
  * `neighboring_qids`:[out] 隣接四角形のIDを含む配列。NULLでも構いませんが、その場合は隣接するIDは収集されません。非NULLの場合、配列は空である必要があり、整数を含みます。注意: エンコーディングはメッシュに保存されているエンコーディングとは異なることに注意してください。TODO: エンコーディングはすべての四角形に対してp4est*meshと同じです。TODO: ゴーストはqidにおけるquad*to*quadの規則を返すことでエンコードできます。ゴースト四角形の場合、p4est*meshの値に-300を加えます。これは、-100未満の値がゴーストに属し、100以上の値がローカルに属することを意味します。正の値はローカル四角形用で、負の値はゴースト四角形を示します。面: 1 .. 8 => 同じサイズの隣接者 (r * 4 + nf) + 1; nf = 0 .. 3 面インデックス; r = 0 .. 1 相対的な向き 9 .. 24 => 二倍サイズの隣接者 9 + h * 8 + r * 4 + nf; h = 0 .. 1 サブ面の番号; r, nf は上記と同じ 25 .. 32 => 半サイズの隣接者 25 + r * 4 + nf; r, nf は上記と同じ コーナー: 1 .. 4 => コーナーのサイズはエンコードされていない nc + 1; nc = 0 .. 3 コーナーインデックス
  * `neighboring_encs`:[out] 隣接四角形のエンコーディングを含む配列。空である必要があり、整数を含みます。

### プロトタイプ

```c
p4est_locidx_t p4est_mesh_get_neighbors (p4est_t * p4est, p4est_ghost_t * ghost, p4est_mesh_t * mesh, p4est_locidx_t curr_quad_id, p4est_locidx_t direction, sc_array_t * neighboring_quads, sc_array_t * neighboring_encs, sc_array_t * neighboring_qids);
```
