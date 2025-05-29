```
TwuAlpha <: TwuAlphaModel
Twu91Alpha = TwuAlpha
TwuAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `M`: 単一パラメータ
  * `N`: 単一パラメータ
  * `L`: 単一パラメータ

## 説明

立方体アルファ `(α(T))` モデル。[`VTPR`](@ref) EoS のデフォルト。Twu-91アルファとしても知られています。

```
αᵢ = Trᵢ^(N*(M-1))*exp(L*(1-Trᵢ^(N*M))
Trᵢ = T/Tcᵢ
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = TwuAlpha("water") #単一入力
alpha = Twu91Alpha("water") #同じ関数
alpha = TwuAlpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = TwuAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","twu.csv"])

# パラメータを直接渡す
alpha = TwuAlpha(["neon","hydrogen"];
    userlocations = (;L = [0.40453, 156.21],
                    M = [0.95861, -0.0062072],
                    N = [0.8396, 5.047])
                )
```

## 参考文献

1. Twu, C. H., Lee, L. L., & Starling, K. E. (1980). 改良されたアルゴン熱力学挙動の解析的表現。流体相平衡, 4(1–2), 35–44. [doi:10.1016/0378-3812(80)80003-3](https://doi.org/10.1016/0378-3812(80)80003-3)
