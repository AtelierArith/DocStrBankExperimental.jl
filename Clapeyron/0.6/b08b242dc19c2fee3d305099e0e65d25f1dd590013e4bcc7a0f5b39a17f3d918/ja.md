```
Twu88Alpha::TwuAlpha

Twu88Alpha(components::Vector{String};
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `M`: 単一パラメータ
  * `N`: 単一パラメータ（オプション）
  * `L`: 単一パラメータ

## モデルパラメータ

  * `M`: 単一パラメータ
  * `N`: 単一パラメータ
  * `L`: 単一パラメータ

## 説明

三次アルファ `(α(T))` モデル。Twu-88アルファとも呼ばれます。

```
αᵢ = Trᵢ^(N*(M-1))*exp(L*(1-Trᵢ^(N*M))
N = 2
Trᵢ = T/Tcᵢ
```

`N` が指定されている場合、デフォルト値の2の代わりに使用されます。

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = Twu88Alpha("water") #単一入力
alpha = Twu88Alpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = Twu88Alpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","twu88.csv"])

# パラメータを直接渡す
alpha = Twu88Alpha(["neon","hydrogen"];
    userlocations = (;L = [0.40453, 156.21],
                    M = [0.95861, -0.0062072],
                    N = [0.8396, 5.047]) #Nを渡さない場合、N = 2と見なされます
                )
```

## 参考文献

1. Twu, C. H., Lee, L. L., & Starling, K. E. (1980). Improved analytical representation of argon thermodynamic behavior. Fluid Phase Equilibria, 4(1–2), 35–44. [doi:10.1016/0378-3812(80)80003-3](https://doi.org/10.1016/0378-3812(80)80003-3)
