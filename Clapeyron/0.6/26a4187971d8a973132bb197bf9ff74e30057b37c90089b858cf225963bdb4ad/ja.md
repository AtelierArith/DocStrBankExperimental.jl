```
PTVAlpha <: PTVAlphaModel

PTVAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。デフォルトは [`PTV`](@ref) EoS。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.46283 + 3.58230Zcᵢ*ωᵢ - 8.19417(Zcᵢ*ωᵢ)^2
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = PTVAlpha("water") #単一入力
alpha = PTVAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = PTVAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = PTVAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
