```
PatelTeja(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = PatelTejaTranslation,
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

## 説明

パテル-テジャ状態方程式。

```
P = RT/(v-b) + a•α(T)/((v - Δ₁b)*(v - Δ₂b))
aᵢᵢ = Ωaᵢ(R²Tcᵢ²/Pcᵢ)
bᵢᵢ = Ωbᵢ(R²Tcᵢ/Pcᵢ)
cᵢ = Ωcᵢ(R²Tcᵢ/Pcᵢ)
Zcᵢ = Pcᵢ*Vcᵢ/(R*Tcᵢ)
Ωaᵢ = 3Zcᵢ² + 3(1 - 2Zcᵢ)Ωbᵢ + Ωbᵢ² + 1 - 3Zcᵢ
0 = -Zcᵢ³ + (3Zcᵢ²)*Ωbᵢ + (2 - 3Zcᵢ)*Ωbᵢ² + Ωbᵢ³
Ωcᵢ = 1 - 3Zcᵢ

γ = ∑cᵢxᵢ/∑bᵢxᵢ
δ = 1 + 6γ + γ²
ϵ = 1 + γ

Δ₁ = -(ϵ + √δ)/2
Δ₂ = -(ϵ - √δ)/2
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = PatelTeja("water") #単一入力
model = PatelTeja(["water","ethanol"]) #複数成分
model = PatelTeja(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更
model = PatelTeja(["water","ethanol"],alpha = TwuAlpha) #アルファ関数の変更
model = PatelTeja(["water","ethanol"],translation = RackettTranslation) #翻訳の変更
model = PatelTeja(["water","ethanol"],mixing = KayRule) #別の混合ルールの使用
model = PatelTeja(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合ルールの使用

# 事前構築されたモデルを渡す

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = PatelTeja(["ethane","butane"],alpha = my_alpha)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = PatelTeja(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = PatelTeja(["neon","hydrogen"];
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

1. Patel, N. C., & Teja, A. S. (1982). A new cubic equation of state for fluids and fluid mixtures. Chemical Engineering Science, 37(3), 463–473. [doi:10.1016/0009-2509(82)80099-7](https://doi.org/10.1016/0009-2509(82)80099-7)
