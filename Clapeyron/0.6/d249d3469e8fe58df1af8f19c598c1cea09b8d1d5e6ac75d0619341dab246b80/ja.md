```
pharmaPCSAFTModel <: PCSAFTModel

pharmaPCSAFT(components;
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー `[K]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - 定数二元相互作用パラメータ（単位なし）
  * `kT`: ペアパラメータ (`Float64`) - T依存の二元相互作用パラメータ `[K^-1]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - 定数二元相互作用パラメータ（単位なし）
  * `kT`: ペアパラメータ (`Float64`) - T依存の二元相互作用パラメータ `[K^-1]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

摂動鎖SAFT (PC-SAFT)、T依存のkijおよびセグメント直径の水の相関 [2]。水のsigma相関を使用するには、`water08`を選択する必要があります。

## 参考文献

1. Paus, R., Ji, Y., Vahle, L., & Sadowski, G. (2015). Predicting the solubility advantage of amorphous pharmaceuticals: A novel thermodynamic approach. Molecular Pharmaceutics, 12(8), 2823–2833. [doi:10.1021/mp500824d](https://doi.org/10.1021/mp500824d)
2. Cameretti, L. F., & Sadowski, G. (2008). Modeling of aqueous amino acid and polypeptide solutions with PC-SAFT. Genie Des Procedes [Chemical Engineering and Processing], 47(6), 1018–1025. [doi:10.1016/j.cep.2007.02.034](https://doi.org/10.1016/j.cep.2007.02.034)
