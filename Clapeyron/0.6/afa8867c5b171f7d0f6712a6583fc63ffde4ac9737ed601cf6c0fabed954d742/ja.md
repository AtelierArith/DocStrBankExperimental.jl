```
PR78Alpha <: PR78AlphaModel

PR78Alpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。デフォルトは [`PR78`](@ref) および [`EPPR78`](@ref) EoS。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
if ωᵢ ≤ 0.491
    mᵢ = 0.37464 + 1.54226ωᵢ - 0.26992ωᵢ^2
else
    mᵢ = 0.379642 + 1.487503ωᵢ - 0.164423ωᵢ^2 - 0.016666ωᵢ^3
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = PR78Alpha("water") #単一入力
alpha = PR78Alpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = PR78Alpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = PR78Alpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
