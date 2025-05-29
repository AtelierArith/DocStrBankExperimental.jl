```
PRAlpha <: SoaveAlphaModel

PRAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

三次のアルファ `(α(T))` モデル。デフォルトは [`PR`](@ref) EoS。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.37464 + 1.54226ωᵢ - 0.26992ωᵢ^2
```

これは `SoaveAlpha` と同等です。

## モデル構築の例

```
# デフォルトのデータベースを使用
alpha = PRAlpha("water") #単一入力
alpha = PRAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = PRAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = PRAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
