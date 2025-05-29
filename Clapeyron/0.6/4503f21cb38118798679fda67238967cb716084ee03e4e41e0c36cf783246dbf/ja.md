```
KUAlpha <: AlphaModel

KUAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。デフォルトは [`KU`](@ref) EoS。

`Tr < 1` の場合

```
αᵢ = (1+mᵢ(1-√(Trᵢ))^nᵢ)^2
Trᵢ = T/Tcᵢ
mᵢ = 0.37790 + 1.51959ωᵢ - 0.46904ωᵢ^2 + 0.015679ωᵢ^3
nᵢ = 0.97016 + 0.05495ωᵢ - 0.1293ωᵢ^2 + 0.0172028ωᵢ^3
```

`Tr > 1` の場合は、`T = Tc` の周りの6次テイラー展開です。

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = KUAlpha("water") #単一入力
alpha = KUAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = KUAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = KUAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## 参考文献

1. Kumar, A., & Upadhyay, R. (2021). A new two-parameters cubic equation of state with benefits of three-parameters. Chemical Engineering Science, 229(116045), 116045. [doi:10.1016/j.ces.2020.116045](https://doi.org/10.1016/j.ces.2020.116045)
