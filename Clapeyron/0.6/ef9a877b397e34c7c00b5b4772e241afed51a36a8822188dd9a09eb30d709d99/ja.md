```
RKPRAlpha <: RKPRAlphaModel

RKPRAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。[`RKPR`](@ref) EoS のデフォルト。

```
αᵢ = (3/(2 + Trᵢ))^kᵢ
kᵢ = (12.504Zc -2.7238) + (7.4513*Zc + 1.9681)ωᵢ + (-2.4407*Zc + 0.0017)ωᵢ^2
Trᵢ = T/Tcᵢ
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = RKPRAlpha("water") #単一入力
alpha = RKPRAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = RKPRAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = RKPRAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
