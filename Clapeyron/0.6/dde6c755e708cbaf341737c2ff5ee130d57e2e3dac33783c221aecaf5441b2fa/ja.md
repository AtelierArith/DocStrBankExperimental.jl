```
BMAlpha <: BMAlphaModel

BMAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

ボストン・マティアス・キュービックアルファ `(α(T))` モデル。

```
if Trᵢ > 1
    αᵢ = (exp((1-2/(2+mᵢ))*(1-Trᵢ^(1+mᵢ/2))))^2
else
    αᵢ = (1+mᵢ*(1-√(Trᵢ)))^2

Trᵢ = T/Tcᵢ

PRモデルの場合:
    mᵢ = 0.37464 + 1.54226ωᵢ - 0.26992ωᵢ^2
RKモデルの場合:
    mᵢ = 0.480 + 1.547ωᵢ - 0.176ωᵢ^2
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = BMAlpha("water") #単一入力
alpha = BMAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = BMAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = BMAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## 参考文献

1. .M. Boston, P.M. Mathias, Proceedings of the 2nd International Conference on Phase Equilibria and Fluid Properties in the Chemical Process Industries, West Berlin, March, 1980, pp. 823–849
