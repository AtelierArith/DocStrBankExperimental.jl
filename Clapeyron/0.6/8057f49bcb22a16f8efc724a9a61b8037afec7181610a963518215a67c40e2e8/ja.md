```
RKPR(components;
idealmodel = BasicIdeal,
alpha = RKPRAlpha,
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
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m3/mol]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション)
  * `l`: ペアパラメータ (`Float64`) (オプション)

## モデルパラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m3/mol]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `a`: ペアパラメータ (`Float64`)
  * `b`: ペアパラメータ (`Float64`)
  * `c`: ペアパラメータ (`Float64`)

## 入力モデル

  * `idealmodel`: 理想モデル
  * `alpha`: アルファモデル
  * `mixing`: 混合モデル
  * `activity`: 混合モデルの作成に使用されるアクティビティモデル。
  * `translation`: 翻訳モデル

## 説明

レドリッヒ-クウォン-ペン-ロビンソン状態方程式。

```
P = RT/(v-b) + a•α(T)/((v + Δ₁b)*(v + Δ₂b))
Δ₁ = δ
Δ₂ = (1 - δ)/(1 + δ)
δ = ∑cᵢxᵢ

aᵢᵢ = Ωaᵢ(R²Tcᵢ²/Pcᵢ)
bᵢᵢ = Ωbᵢ(R²Tcᵢ/Pcᵢ)
Ωaᵢ = (3*yᵢ^2 + 3yᵢdᵢ + dᵢ^2 + dᵢ - 1)/(3yᵢ + dᵢ - 1)^2
Ωbᵢ = 1/(3yᵢ + dᵢ - 1)
dᵢ = (1 + cᵢ^2)/(1 + cᵢ)
yᵢ = 1 + (2(1 + cᵢ))^(1/3) + (4/(1 + cᵢ))^(1/3)
```

`cᵢ`は次のようにフィッティングされます：

```
if Zcᵢ[exp] > 0.29
    cᵢ = √2 - 1
else
    Zcᵢ = 1.168Zcᵢ[exp]
    f(cᵢ) == 0
    f(cᵢ) = Zcᵢ - yᵢ/(3yᵢ + dᵢ - 1)
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = RKPR("water") #単一入力
model = RKPR(["water","ethanol"]) #複数成分
model = RKPR(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更
model = RKPR(["water","ethanol"],alpha = TwuAlpha) #アルファ関数の変更
model = RKPR(["water","ethanol"],translation = RackettTranslation) #翻訳の変更
model = RKPR(["water","ethanol"],mixing = KayRule) #別の混合ルールの使用
model = RKPR(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合ルールの使用

# 事前構築されたモデルを渡す

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = RKPR(["ethane","butane"],alpha = my_alpha)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = RKPR(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = RKPR(["neon","hydrogen"];
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

1. Cismondi, M., & Mollerup, J. (2005). Development and application of a three-parameter RK–PR equation of state. Fluid Phase Equilibria, 232(1–2), 74–89. [doi:10.1016/j.fluid.2005.03.020](https://doi.org/10.1016/j.fluid.2005.03.020)
2. Tassin, N. G., Mascietti, V. A., & Cismondi, M. (2019). Phase behavior of multicomponent alkane mixtures and evaluation of predictive capacity for the PR and RKPR EoS’s. Fluid Phase Equilibria, 480, 53–65. [doi:10.1016/j.fluid.2018.10.005](https://doi.org/10.1016/j.fluid.2018.10.005)
