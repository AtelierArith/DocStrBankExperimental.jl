```
SAFTgammaMie <: SAFTModel
```

SAFTgammaMie(components;     idealmodel = BasicIdeal,     userlocations = String[],     group*userlocations = String[],     ideal*userlocations = String[],     epsilon*mixing = :default,     reference*state = nothing,     verbose = false,     assoc_options = AssocOptions())

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `vst`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `S`: 単一パラメータ (`Float64`) - セグメントの形状因子（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## モデルパラメータ

  * `segment`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `shapefactor`: 単一パラメータ (`Float64`) - セグメントの形状因子（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積
  * `mixed_segment`: 混合グループ寄与パラメータ: ∑nᵢₖνₖmₖ

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

SAFT-γ-Mie EoS

!!! info
    Hudsen-McCoubrey結合則（`√(ϵᵢ*ϵⱼ)*(σᵢ^3 * σⱼ^3)/σᵢⱼ^6`）またはデフォルトのルール（`√(ϵᵢ*ϵⱼ*(σᵢ^3 * σⱼ^3))/σᵢⱼ^3`）のいずれかを選択できます。`epsilon_mixing`引数に`:default`または`:hudsen_mccoubrey`を渡すことで選択できます。


## 参考文献

1. Papaioannou, V., Lafitte, T., Avendaño, C., Adjiman, C. S., Jackson, G., Müller, E. A., & Galindo, A. (2014). Group contribution methodology based on the statistical associating fluid theory for heteronuclear molecules formed from Mie segments. The Journal of Chemical Physics, 140(5), 054107. [doi:10.1063/1.4851455](https://doi.org/10.1063/1.4851455)
2. Dufal, S., Papaioannou, V., Sadeqzadeh, M., Pogiatzis, T., Chremos, A., Adjiman, C. S., … Galindo, A. (2014). Prediction of thermodynamic properties and phase behavior of fluids and mixtures with the SAFT-γ Mie group-contribution equation of state. Journal of Chemical and Engineering Data, 59(10), 3272–3288. [doi:10.1021/je500248h](https://doi.org/10.1021/je500248h)

## 利用可能なグループのリスト

|     名前 |          説明 |
| ------:| -----------:|
|    CH3 |         メチル |
|    CH2 |        メチレン |
|     CH |             |
|      C |             |
|    aCH |      芳香族 CH |
|  aCCH2 |             |
|   aCCH |             |
|   CH2= |       アルケン群 |
|    CH= |             |
|   cCH2 |     環状アルカン群 |
|   COOH |      カルボン酸群 |
|    COO |       エステル群 |
|     OH |      ヒドロキシル |
|  CH2OH | メチレンヒドロキシル群 |
|   CHOH |             |
|    NH2 |        アミン群 |
|     NH |             |
|      N |             |
|    cNH |             |
|     cN |             |
|    CH= |             |
|  aCCH3 |             |
|   aCOH |             |
|    cCH |             |
|  cCHNH |             |
|   cCHN |             |
| aCCOaC |             |
| aCCOOH |             |
| aCNHaC |             |
|  CH3CO |             |
|     eO |   エンドエーテル酸素 |
|     cO |  センターエーテル酸素 |
