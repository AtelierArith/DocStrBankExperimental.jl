```
PTV(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = PTVTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
verbose = false,
reference_state = nothing)
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

パテル-テハ-バルデラマ状態方程式。

```
P = RT/(v-b) + a•α(T)/((v - Δ₁b)*(v - Δ₂b))
aᵢᵢ = Ωaᵢ(R²Tcᵢ²/Pcᵢ)
bᵢᵢ = Ωbᵢ(R²Tcᵢ/Pcᵢ)
cᵢ = Ωcᵢ(R²Tcᵢ/Pcᵢ)
Zcᵢ = Pcᵢ*Vcᵢ/(R*Tcᵢ)
Ωaᵢ = 0.66121 - 0.76105Zcᵢ
Ωbᵢ = 0.02207 + 0.20868Zcᵢ
Ωcᵢ = 0.57765 - 1.87080Zcᵢ

γ = ∑cᵢxᵢ/∑bᵢxᵢ
δ = 1 + 6γ + γ²
ϵ = 1 + γ

Δ₁ = -(ϵ + √δ)/2
Δ₂ = -(ϵ - √δ)/2
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = PTV("water") #単一入力
model = PTV(["water","ethanol"]) #複数成分
model = PTV(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更
model = PTV(["water","ethanol"],alpha = TwuAlpha) #アルファ関数の変更
model = PTV(["water","ethanol"],translation = RackettTranslation) #翻訳の変更
model = PTV(["water","ethanol"],mixing = KayRule) #別の混合ルールの使用
model = PTV(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合ルールの使用

# 事前構築されたモデルを渡す

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = PTV(["ethane","butane"],alpha = my_alpha)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = PTV(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = PTV(["neon","hydrogen"];
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

1. Valderrama, J. O. (1990). A generalized Patel-Teja equation of state for polar and nonpolar fluids and their mixtures. Journal of Chemical Engineering of Japan, 23(1), 87–91. [doi:10.1252/jcej.23.87](https://doi.org/10.1252/jcej.23.87)
