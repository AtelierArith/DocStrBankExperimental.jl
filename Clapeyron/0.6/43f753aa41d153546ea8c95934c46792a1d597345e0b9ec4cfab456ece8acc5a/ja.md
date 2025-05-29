```
SoaveAlpha <: SoaveAlphaModel

SoaveAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。デフォルトは [`SRK`](@ref) EoS。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.480 + 1.547ωᵢ - 0.176ωᵢ^2
```

`mᵢ` に異なる多項式係数を使用するには、`Clapeyron.α_m(::CubicModel,::SoaveAlphaModel) = (c₁,c₂,...cₙ)` をオーバーロードします。

## モデル構築の例

```
# デフォルトのデータベースを使用
alpha = SoaveAlpha("water") #単一入力
alpha = SoaveAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = SoaveAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = SoaveAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
