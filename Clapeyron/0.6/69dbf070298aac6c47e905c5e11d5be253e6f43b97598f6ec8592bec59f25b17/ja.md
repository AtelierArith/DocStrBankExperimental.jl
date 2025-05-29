MTTranslation <: MTTranslationModel

```
MTTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

マゴラス・タッシオス翻訳モデル（立方体用）:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = T₀ᵢ+(T̄cᵢ-T̄₀ᵢ)*exp(β*abs(1-Trᵢ))
Trᵢ = T/T̄cᵢ
T̄cᵢ = (RTcᵢ/Pcᵢ)*(0.3074-Zcᵢ)
T̄₀ᵢ = (RTcᵢ/Pcᵢ)*(-0.014471 + 0.067498ωᵢ - 0.084852ωᵢ^2 + 0.067298ωᵢ^3 - 0.017366ωᵢ^4)
Zcᵢ = 0.289 - 0.0701ωᵢ - 0.0207ωᵢ^2
βᵢ  = -10.2447 - 28.6312ωᵢ
```

## モデル構築の例

```
# デフォルトデータベースを使用
translation = MTTranslation("water") #単一入力
translation = MTTranslation(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
translation = MTTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
translation = MTTranslation(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## 参考文献

1. Magoulas, K., & Tassios, D. (1990). Thermophysical properties of n-Alkanes from C1 to C20 and their prediction for higher ones. Fluid Phase Equilibria, 56, 119–140. [doi:10.1016/0378-3812(90)85098-u](https://doi.org/10.1016/0378-3812(90)85098-u)
