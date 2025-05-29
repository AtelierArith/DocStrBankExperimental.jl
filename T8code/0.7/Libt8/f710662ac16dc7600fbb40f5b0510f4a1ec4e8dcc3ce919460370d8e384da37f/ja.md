```
t8_cmesh_set_join_by_vertices(cmesh, ntrees, eclasses, vertices, connectivity, do_both_directions)
```

未コミットの面接続情報を、ツリー頂点のリストに基づいて設定します。

!!! warning
    このルーチンは非常に大きなメッシュに対しては高コストになる可能性があります。この場合、完全な機能を持つメッシュジェネレーターの使用を検討してください。


!!! note
    このルーチンは周期境界を検出しません。


# 引数

  * `cmesh`:[in,out] t8code cmeshオブジェクトへのポインタ。NULLに設定された場合、この引数は無視されます。
  * `ntrees`:[in] 粗いメッシュ要素、すなわちツリーの数。
  * `vertices`:[in] 次元が [ntrees,[`T8_ECLASS_MAX_CORNERS`](@ref),[`T8_ECLASS_MAX_DIM`](@ref)] の要素ごとの頂点のリスト。
  * `eclasses`:[in] 長さ [ntrees] の要素クラスのリスト。
  * `connectivity`:[in,out] connectivity が NULL でない場合、変数は割り当てられた面接続配列へのポインタで埋められます。この配列の所有権は呼び出し元に移ります。この引数は主にデバッグおよびテスト目的で使用されます。*connectivity* の次元は [ntrees,[`T8_ECLASS_MAX_FACES`](@ref),3] です。各要素および各面について、次の情報が保存されます: neighbor*tree*id, neighbor*dual*face_id, orientation
  * `do_both_directions`:[in] 両方の隣接側から接続性を計算します。計算にかかる時間が大幅に長くなります。

### プロトタイプ

```c
void t8_cmesh_set_join_by_vertices (t8_cmesh_t cmesh, const t8_gloidx_t ntrees, const t8_eclass_t *eclasses, const double *vertices, int **connectivity, const int do_both_directions);
```
