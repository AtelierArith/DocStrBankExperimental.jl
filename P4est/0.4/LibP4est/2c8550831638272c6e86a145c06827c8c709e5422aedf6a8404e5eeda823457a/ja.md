```
p8est_quadrant_set_morton_ext128(quadrant, level, id)
```

与えられた線形位置に基づいて四分木のモートンインデックスを設定します。これは、p4est*quadrant*linear_idの逆操作です。

!!! note
    *quadrant*のuser_dataは決して変更されません。


### パラメータ

  * `quadrant`:[in,out] モートンインデックスが設定される四分木。
  * `level`:[in] グリッドおよび結果の四分木のレベル。
  * `id`:[in] 一様グリッド上の四分木の線形インデックス。

### プロトタイプ

```c
void p8est_quadrant_set_morton_ext128 (p8est_quadrant_t * quadrant, int level, const p8est_lid_t * id);
```
