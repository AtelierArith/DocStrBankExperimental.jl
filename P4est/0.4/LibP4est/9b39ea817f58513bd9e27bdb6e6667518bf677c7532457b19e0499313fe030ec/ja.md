```
p4est_mesh_new(p4est_, ghost, btype)
```

p4est*mesh 構造体を作成します。この関数は quad*to*tree および quad*level フィールドを設定しません。それらを設定するには、p4est*mesh*new_ext を使用してください。

### パラメータ

  * `p4est`:[in] 完全に 2:1 バランスの取れたフォレスト。
  * `ghost`:[in] 提供された `p4est` から作成されたゴーストレイヤー。
  * `btype`:[in] 隣接するノードの最高コーディメンションを決定します。

### 戻り値

完全に割り当てられたメッシュ構造体。

### プロトタイプ

```c
p4est_mesh_t *p4est_mesh_new (p4est_t * p4est, p4est_ghost_t * ghost, p4est_connect_type_t btype);
```
