```
VTPRUNIFACModel <: UNIFACModel

VTPRUNIFAC(components;
puremodel = BasicIdeal,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `Q`: 単一パラメータ (`Float64`) - 正規化されたグループ表面積
  * `A`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `B`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `C`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

UNIFAC (UNIQUAC 機能群活動係数) 活動モデル。

修正UNIFAC (ドルトムント) 実装、残差部分のみ、ボリューム変換ペン-ロビンソン (VTPR) EoS に使用される活動モデル。

残差部分は成分の代わりにグループを反復処理します。

```
Gᴱ = nRT(gᴱ(res))
gᴱ(res) = -v̄∑XₖQₖlog(∑ΘₘΨₘₖ)
v̄ = ∑∑xᵢνᵢₖ for k ∈ groups,  for i ∈ components
Xₖ = (∑xᵢνᵢₖ)/v̄ for i ∈ components
Θₖ = QₖXₖ/∑QₖXₖ
Ψₖₘ = exp(-(Aₖₘ + BₖₘT + CₖₘT²)/T)
```

## 参考文献

1. Fredenslund, A., Gmehling, J., Michelsen, M. L., Rasmussen, P., & Prausnitz, J. M. (1977). UNIFAC グループ寄与法を用いた多成分蒸留塔のコンピュータ設計による活動係数の計算。Industrial & Engineering Chemistry Process Design and Development, 16(4), 450–462. "doi:[10.1021/i260064a004](https://doi.org/10.1021/i260064a004)"
2. Weidlich, U.; Gmehling, J. 修正UNIFACモデル。1. VLE、hE、および.gamma..infin.の予測。Ind. Eng. Chem. Res. 1987, 26, 1372–1381.
3. Ahlers, J., & Gmehling, J. (2001). 普遍的なグループ寄与状態方程式の開発。Fluid Phase Equilibria, 191(1–2), 177–188. [doi:10.1016/s0378-3812(01)00626-4](https://doi.org/10.1016/s0378-3812(01)00626-4)

```
