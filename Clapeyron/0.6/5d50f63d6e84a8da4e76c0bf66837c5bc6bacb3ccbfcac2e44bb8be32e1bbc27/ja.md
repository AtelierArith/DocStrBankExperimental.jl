```
UNIFACFVModel <: ActivityModel

UNIFACFV(components;
puremodel = PR,
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `volume`: 単一パラメータ (`Float64`)  - 種の特定体積 `[g/cm^3]`
  * `R`: 単一パラメータ (`Float64`)  - 正規化されたグループのファンデルワールス体積
  * `Q`: 単一パラメータ (`Float64`) - 正規化されたグループの表面積
  * `A`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `Mw`: 単一パラメータ (`Float64`) - グループの分子量

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

UNIFACFV (UNIFAC自由体積) 活動モデル。溶媒-ポリマー混合物に特化しています。

組み合わせ部分は、GC平均修正[`UNIQUAC`](@ref)モデルに対応しています。

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res) + gᴱ(FV))
```

## 参考文献

```
