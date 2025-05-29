```
PatelTejaAlpha <: SoaveAlphaModel

PatelTejaAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。 [`PatelTeja`](@ref) EoS のデフォルト。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.452413 + 1.30982ωᵢ - 0.295937ωᵢ^2
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = PatelTejaAlpha("water") #単一入力
alpha = PatelTejaAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = PatelTejaAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = PatelTejaAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
