```
ogUNIFACModel <: UNIFACModel

ogUNIFAC(components;
puremodel = PR, 
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `R`: 単一パラメータ (`Float64`)  - 正規化されたグループのバン・デル・ワールス体積
  * `Q`: 単一パラメータ (`Float64`) - 正規化されたグループの表面積
  * `A`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

UNIFAC (UNIQUAC機能群活動係数) 活動モデル。

元の定式化。

組み合わせ部分は、GC平均修正UNIQUACモデルに対応しています。残差部分は成分の代わりにグループを反復します。

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res))
```

組み合わせ部分:

```
gᴱ(comb) = ∑[xᵢlog(Φᵢ/xᵢ) + 5qᵢxᵢlog(θᵢ/Φᵢ)]
θᵢ = qᵢxᵢ/∑qᵢxᵢ
Φᵢ = rᵢxᵢ/∑rᵢxᵢ
rᵢ = ∑Rₖνᵢₖ for k ∈ groups
qᵢ = ∑Qₖνᵢₖ for k ∈ groups
```

残差部分:

```
gᴱ(residual) = -v̄∑XₖQₖlog(∑ΘₘΨₘₖ)
v̄ = ∑∑xᵢνᵢₖ for k ∈ groups,  for i ∈ components
Xₖ = (∑xᵢνᵢₖ)/v̄ for i ∈ components 
Θₖ = QₖXₖ/∑QₖXₖ
Ψₖₘ = exp(-(Aₖₘ/T)
```

## 参考文献

1. Fredenslund, A., Gmehling, J., Michelsen, M. L., Rasmussen, P., & Prausnitz, J. M. (1977). Computerized design of multicomponent distillation columns using the UNIFAC group contribution method for calculation of activity coefficients. Industrial & Engineering Chemistry Process Design and Development, 16(4), 450–462. [doi:10.1021/i260064a004](https://doi.org/10.1021/i260064a004)
