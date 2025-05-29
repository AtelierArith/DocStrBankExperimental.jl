```
p4est_quadrant_exists(p4est_, ghost, treeid, q, exists_arr, rproc_arr, rquad_arr)
```

ローカルフォレストまたはゴーストレイヤーに四分木が存在するかどうかを確認します。

木のコーナーをまたぐ四分木については、四分木がコーナー隣接ノードのいずれかに存在するかどうかを確認するため、複数のクエリを実行できます。

### パラメータ

  * `p4est`:[in] *q* を検索するフォレスト
  * `ghost`:[in] *q* を検索するゴーストレイヤー
  * `treeid`:[in] *q* が属する木（拡張可能）。
  * `q`:[in] 検索されている四分木。
  * `exists_arr`:[in,out] 存在する必要があり、elem_size = sizeof (int) である必要があります（木をまたぐコーナーケース用）。この関数によって、各コーナー検索のために1エントリにリサイズされ、ローカルフォレストまたはゴーストレイヤーに存在するかどうかに応じてtrue/falseに設定されます。
  * `rproc_arr`:[in,out] NULLでない場合、クエリごとに1ランクで埋められます。
  * `rquad_arr`:[in,out] NULLでない場合、クエリごとに1四分木で埋められます。そのpiggy3メンバーも定義されます。

### 戻り値

四分木がローカルフォレストまたはゴーストレイヤーに存在する場合はtrue、どちらにも存在しない場合はfalseを返します。

### プロトタイプ

```c
int p4est_quadrant_exists (p4est_t * p4est, p4est_ghost_t * ghost, p4est_topidx_t treeid, const p4est_quadrant_t * q, sc_array_t * exists_arr, sc_array_t * rproc_arr, sc_array_t * rquad_arr);
```
