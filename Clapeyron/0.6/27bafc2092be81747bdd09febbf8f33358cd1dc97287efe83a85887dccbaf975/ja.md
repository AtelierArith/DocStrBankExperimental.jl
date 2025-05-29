```
Berthelot(components;
idealmodel = BasicIdeal,
alpha = ClausiusAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `Vc`: 単一パラメータ (`Float64`) - モル体積 `[m^3/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション)

## モデルパラメータ

  * `a`: ペアパラメータ (`Float64`)
  * `b`: ペアパラメータ (`Float64`)
  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Vc`: 単一パラメータ (`Float64`) - モル体積 `[m^3/mol]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## 入力モデル

  * `idealmodel`: 理想モデル
  * `alpha`: アルファモデル
  * `mixing`: 混合モデル
  * `activity`: 活動モデル、混合モデルの作成に使用されます。
  * `translation`: 翻訳モデル

## 説明

バーテロ方程式。体積-圧力に基づく混合則を使用します。すなわち：

```
a = 8*Pc*Vc^2
b = Vc/3
R = (8/3)*Pc*Vc/Tc
P = RT/(V-Nb) + a•α(T)/V²
α(T) = Tc/T
```

## 参考文献

1. Berthelot, D. (1899). Sur une méthode purement physique pour la détermination des poids moléculaires des gaz et des poids atomiques de leurs éléments. Journal de Physique Théorique et Appliquée, 8(1), 263–274. [doi:10.1051/jphystap:018990080026300](https://doi.org/10.1051/jphystap:018990080026300)
