```
p8est_face_quadrant_exists(p8est_, ghost, treeid, q, face, hang, owner_rank)
```

ローカルフォレストまたはゴーストレイヤーに四分木が存在するかどうかを確認します。

ツリー境界を越える四分木については、エッジやコーナーを越えずに、任意の面を越えて四分木が存在するかどうかを確認します。

### パラメータ

  * `p8est`:[in] *q* を検索するフォレスト。
  * `ghost`:[in] *q* を検索するゴーストレイヤー。
  * `treeid`:[in] *q* が属するツリー。
  * `q`:[in] 検索されている四分木。
  * `face`:[in,out] 入力時、*q* が作成された面のID。出力時、隣接する面の番号に方向を加えたものが格納され、面は 0..23 の範囲になります。
  * `hang`:[in,out] NULLでない場合、*q* が元の四分木よりも大きいことを示します。その元の四分木の子IDがhangに渡されます。出力時、hangには* q* がその起源と接触しているハンギング面の番号が保持されます。
  * `owner_rank`:[out] 見つかった場合はオーナーのランクで埋められ、見つからない場合は未定義です。

### 戻り値

ローカルフォレストまたはゴーストレイヤーに四分木が存在する場合は、*q* のローカル番号を返します。そうでない場合、ドメイン境界には -2 を、見つからない場合には -1 を返します。

### プロトタイプ

```c
p4est_locidx_t p8est_face_quadrant_exists (p8est_t * p8est, p8est_ghost_t * ghost, p4est_topidx_t treeid, const p8est_quadrant_t * q, int *face, int *hang, int *owner_rank);
```
