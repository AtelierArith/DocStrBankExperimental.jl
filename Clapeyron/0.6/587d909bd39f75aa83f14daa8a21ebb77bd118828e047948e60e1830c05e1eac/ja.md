```
Clausius(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = ClausiusTranslation,
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
  * `Vc`: 単一パラメータ (`Float64`) - モル体積 `[m^3/mol]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション)
  * `l`: ペアパラメータ (`Float64`) (オプション)

## モデルパラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Vc`: 単一パラメータ (`Float64`) - モル体積 `[m^3/mol]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `a`: ペアパラメータ (`Float64`)
  * `b`: ペアパラメータ (`Float64`)

## 説明

クラウジウス状態方程式。

```
P = RT/(v-b) + a•α(T)/((v - Δ₀b)^2)

aᵢᵢ =27/64 * (RTcᵢ)²/Pcᵢ
bᵢᵢ = Vcᵢ - 1/4 * RTcᵢ/Pcᵢ
cᵢ = 3/8 * RTcᵢ/Pcᵢ - Vcᵢ

Δ₀ = ∑cᵢxᵢ/∑bᵢxᵢ

```

## 参考文献

1. Clausius, R. (1880). Ueber das Verhalten der Kohlensäure in Bezug auf Druck, Volumen und Temperatur. Annalen der Physik, 245(3), 337–357. [doi:10.1002/andp.18802450302](https://doi.org/10.1002/andp.18802450302)
