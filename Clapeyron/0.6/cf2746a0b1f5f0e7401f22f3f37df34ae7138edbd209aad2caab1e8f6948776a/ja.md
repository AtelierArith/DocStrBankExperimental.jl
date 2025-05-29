```
MTAlpha <: MTAlphaModel

MTAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

Magoulas & Tassios Cubic alpha `(α(T))` モデル。 [`UMRPR`](@ref) EoS のデフォルト。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.384401 + 1.52276ωᵢ - 0.213808ωᵢ^2 + 0.034616ωᵢ^3 - 0.001976ωᵢ^4 
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = MTAlpha("water") #単一入力
alpha = MTAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = MTAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = MTAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## 参考文献

1. Magoulas, K., & Tassios, D. (1990). Thermophysical properties of n-Alkanes from C1 to C20 and their prediction for higher ones. Fluid Phase Equilibria, 56, 119–140. [doi:10.1016/0378-3812(90)85098-u](https://doi.org/10.1016/0378-3812(90)85098-u)
