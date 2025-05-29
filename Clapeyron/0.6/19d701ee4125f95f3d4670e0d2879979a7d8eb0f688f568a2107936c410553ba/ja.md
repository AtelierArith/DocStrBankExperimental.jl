```
KU(components;
idealmodel = BasicIdeal,
alpha = KUAlpha,
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
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m^3]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション)
  * `l`: ペアパラメータ (`Float64`) (オプション)

## モデルパラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m^3]`
  * `omega_a`: 単一パラメータ (`Float64`) - 臨界定数 a - 単位なし
  * `omega_b`: 単一パラメータ (`Float64`) - 臨界定数 b - 単位なし
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `a`: ペアパラメータ (`Float64`)
  * `b`: ペアパラメータ (`Float64`)

## 入力モデル

  * `idealmodel`: 理想モデル
  * `alpha`: アルファモデル
  * `mixing`: 混合モデル
  * `activity`: 活動モデル、混合モデルの作成に使用される。
  * `translation`: 翻訳モデル

## 説明

クマール-ウパディヤイ立方体状態方程式。`Ωa` と `Ωb` は成分依存

```
P = RT/(v-b) + a•κ(T)/((v²-1.6bv - 0.8b²)
a = Ωa(R²Tcᵢ²/Pcᵢ)
b = Ωb(R²Tcᵢ²/Pcᵢ)
Ωa = Zc[(1 + 1.6α - 0.8α²)²/((1 - α²)(2 + 1.6α))]
χ = ∛[√(1458Zc³ - 1701Zc² + 540Zc -20)/32√3Zc² - (729Zc³ - 216Zc + 8)/1728Zc³]
α = [χ + (81Zc² - 72Zc + 4)/144Zc²χ + (3Zc - 2)/12Zc]
Ωa = Zc[(1 + 1.6α - 0.8α²)²/((1 - α²)(2 + 1.6α))]
Ωb = αZc
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = KU("water") #単一入力
model = KU(["water","ethanol"]) #複数成分
model = KU(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更
model = KU(["water","ethanol"],alpha = TwuAlpha) #アルファ関数の変更
model = KU(["water","ethanol"],translation = RackettTranslation) #翻訳の変更
model = KU(["water","ethanol"],mixing = KayRule) #別の混合ルールの使用
model = KU(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合ルールの使用

# 事前構築されたモデルを渡す

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = KU(["ethane","butane"],alpha = my_alpha)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = KU(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = KU(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Vc = [4.25e-5, 6.43e-5],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,lは単一成分モデルでは省略可能。
                        l = [0. 0.01; 0.01 0.])
                    )
```

## 参考文献

1. Kumar, A., & Upadhyay, R. (2021). A new two-parameters cubic equation of state with benefits of three-parameters. Chemical Engineering Science, 229(116045), 116045. [doi:10.1016/j.ces.2020.116045](https://doi.org/10.1016/j.ces.2020.116045)
