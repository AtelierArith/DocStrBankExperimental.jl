```
PSRKUNIFAC(components;
puremodel = BasicIdeal,
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `R`: 単一パラメータ (`Float64`)  - 正規化されたグループ・ヴァン・デル・ワールス体積
  * `Q`: 単一パラメータ (`Float64`) - 正規化されたグループ表面積
  * `A`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `B`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `C`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

UNIFAC (UNIQUAC機能群活動係数) 活動モデル。

修正された [UNIFAC](@ref) (ドルトムント) 実装で、予測的ソアヴェ-レドリッヒ-クワン (PSRK) EoS に合わせてパラメータが調整されています。

## 参考文献

1. Fredenslund, A., Gmehling, J., Michelsen, M. L., Rasmussen, P., & Prausnitz, J. M. (1977). UNIFACグループ寄与法を用いた多成分蒸留塔のコンピュータ設計による活動係数の計算。Industrial & Engineering Chemistry Process Design and Development, 16(4), 450–462. [doi:10.1021/i260064a004](https://doi.org/10.1021/i260064a004)
2. Weidlich, U.; Gmehling, J. 修正されたUNIFACモデル。1. VLE、hE、および.gamma..infin.の予測。Ind. Eng. Chem. Res. 1987, 26, 1372–1381.
3. Horstmann, S., Jabłoniec, A., Krafczyk, J., Fischer, K., & Gmehling, J. (2005). PSRKグループ寄与状態方程式: 包括的な改訂と拡張IV、1000成分のための臨界定数とα関数パラメータを含む。Fluid Phase Equilibria, 227(2), 157–164. [doi:10.1016/j.fluid.2004.11.002](https://doi.org/10.1016/j.fluid.2004.11.002)

```
