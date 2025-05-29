```
p8est_mesh_new(p8est_, ghost, btype)
```

p8est*mesh 構造体を作成します。この関数は quad*to*tree および quad*level フィールドを設定しません。それらを設定するには、p8est*mesh*new_ext を使用してください。

### パラメータ

  * `p8est`:[in] 完全に 2:1 バランスの取れたフォレスト。
  * `ghost`:[in] 提供された `p4est` から作成されたゴーストレイヤー。
  * `btype`:[in] 隣接する要素の最高コーディメンションを決定します。

### 戻り値

完全に割り当てられたメッシュ構造体。

### プロトタイプ

```c
p8est_mesh_t *p8est_mesh_new (p8est_t * p8est, p8est_ghost_t * ghost, p8est_connect_type_t btype);
```
