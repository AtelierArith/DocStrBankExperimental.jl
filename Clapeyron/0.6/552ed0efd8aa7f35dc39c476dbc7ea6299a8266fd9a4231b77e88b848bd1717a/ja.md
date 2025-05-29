```
CPAModel <: EoSModel

function CPA(components;
    radial_dist::Symbol = :CS,
    idealmodel = BasicIdeal,
    cubicmodel = RK,
    alpha = sCPAAlpha,
    mixing = vdW1fRule,
    activity = nothing,
    translation = NoTranslation,
    userlocations = String[],
    ideal_userlocations = String[],
    alpha_userlocations = String[],
    activity_userlocations = String[],
    mixing_userlocations = String[],
    translation_userlocations = String[],
    reference_state = nothing,
    verbose = false,
    assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `a`: 単一パラメータ (`Float64`) - 引力パラメータ `[m^6*Pa/mol]`
  * `b`: 単一パラメータ (`Float64`) - コボリューム `[m^3/mol]`
  * `c1`: 単一パラメータ (`Float64`) - α関数定数パラメータ（単位なし）
  * `k`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `l`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 削減アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーションボリューム `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `a`: ペアパラメータ (`Float64`) - 混合引力パラメータ `[m^6*Pa/mol]`
  * `b`: ペアパラメータ (`Float64`) - 混合コボリューム `[m^3/mol]`
  * `c1`: 単一パラメータ (`Float64`) - α関数定数パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 削減アソシエーションエネルギー `[J]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーションボリューム `[m^3]`

## 入力モデル

  * `idealmodel`: 理想モデル
  * `cubicmodel`: 立方体モデル

## 説明

Cubic Plus Association (CPA) EoS。立方体部分とアソシエーション部分の追加から成る：

```
a_res(model::CPA) = a_res(model::Cubic) + a_assoc(model)
```

`radial_dist` 引数は、カルナハン-スターリング形式（`CS`、デフォルト）またはコントゲオルギス（`KG`）項、より広く知られているs-CPAの間で選択するために使用できます。

## 参考文献

1. Kontogeorgis, G. M., Michelsen, M. L., Folas, G. K., Derawi, S., von Solms, N., & Stenby, E. H. (2006). CPA（立方体プラスアソシエーション）状態方程式との10年間。パート1。純粋な化合物と自己アソシエーション系。Industrial & Engineering Chemistry Research, 45(14), 4855–4868. [doi:10.1021/ie051305v](https://doi.org/10.1021/ie051305v)

```
