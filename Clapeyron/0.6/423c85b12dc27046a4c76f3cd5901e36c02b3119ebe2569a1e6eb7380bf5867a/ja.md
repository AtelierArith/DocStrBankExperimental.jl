```
CPAAlpha <: CPAAlphaModel

CPAAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `c1`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。`CPA` EoS のデフォルト。

```
αᵢ = (1+c¹ᵢ(1-√(Trᵢ)))^2
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = CPAAlpha("water") #単一入力
alpha = CPAAlpha(["water","carbon dioxide"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = CPAAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","cpa/alpha.csv"])

# パラメータを直接渡す
alpha = CPAAlpha(["water","carbon dioxide"];userlocations = (;c1 = [0.67,0.76]))
```
