```
p4est_quadrant_linear_id_ext128(quadrant, level, id)
```

均一グリッドにおける四分木の線形位置を [`p4est_lid_t`](@ref) として計算します。グリッドと四分木のレベルは一致する必要はありません。一致する場合、これは p4est*quadrant*set_morton の逆です。

!!! note
    *quadrant* の user_data は決して変更されません。


### パラメータ

  * `quadrant`:[in] 線形インデックスが計算される四分木。四分木がグリッドよりも小さい場合（quadrant->level が高い）、結果はグリッドのレベルでのその祖先から計算されます。四分木がグリッドよりも小さいレベルを持つ場合（グリッドセルよりも大きい）、その左下隅を共有するグリッドセルが参照として使用されます。
  * `level`:[in] 線形位置が計算される正規グリッドのレベル。
  * `id`:[in,out] 割り当てられたまたは静的な [`p4est_lid_t`](@ref) へのポインタ。id は均一グリッド上のこの四分木の線形位置になります。

### プロトタイプ

```c
void p4est_quadrant_linear_id_ext128 (const p4est_quadrant_t * quadrant, int level, p4est_lid_t * id);
```
