```
p8est_connectivity_join_faces(conn, tree_left, tree_right, face_left, face_right, orientation)
```

[`p8est_connectivity_join_faces`](@ref) この関数は、既存の有効な接続 *conn* を取り、現在境界面である2つの木の面を結合することによって修正します。

### パラメータ

  * `conn`:[in,out] 変更される接続。
  * `tree_left`:[in] 結合された面の左側にある木。
  * `tree_right`:[in] 結合された面の右側にある木。
  * `face_left`:[in] 結合される *tree_left* の面。
  * `face_right`:[in] 結合される *tree_right* の面。
  * `orientation`:[in] 結合後の *face_left* と *face_right* の向き（向きを理解するために [`p8est_connectivity_t`](@ref) の説明を参照してください）。

### プロトタイプ

```c
void p8est_connectivity_join_faces (p8est_connectivity_t * conn, p4est_topidx_t tree_left, p4est_topidx_t tree_right, int face_left, int face_right, int orientation);
```
