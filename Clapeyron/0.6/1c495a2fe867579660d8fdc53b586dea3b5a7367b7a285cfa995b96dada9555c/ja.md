```
Soave2019Alpha <: SoaveAlphaModel

Soave2019Alpha(components::Vector{String};
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `acentricfactor`: 単一パラメータ (`Float64`)

## 説明

立方体アルファ `(α(T))` モデル。重い分子に対してより良い結果を得るために `PR` および `SRK` の m(ω) 相関を更新しました。

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.37464 + 1.54226ωᵢ - 0.26992ωᵢ^2
```

ここで、ペン-ロビンソンの場合:

```
mᵢ = 0.3919 + 1.4996ωᵢ - 0.2721ωᵢ^2 + 0.1063ωᵢ^3
```

および、レドリッヒ-クワンの場合:

```
mᵢ = 0.4810 + 1.5963ωᵢ - 0.2963ωᵢ^2 + 0.1223ωᵢ^3
```

## モデル構築の例

```
# デフォルトデータベースを使用
alpha = Soave2019Alpha("water") #単一入力
alpha = Soave2019Alpha(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
alpha = Soave2019Alpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# パラメータを直接渡す
alpha = Soave2019Alpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## 参考文献

1. Pina-Martinez, A., Privat, R., Jaubert, J.-N., & Peng, D.-Y. (2019). Updated versions of the generalized Soave α-function suitable for the Redlich-Kwong and Peng-Robinson equations of state. Fluid Phase Equilibria, 485, 264–269. [doi:10.1016/j.fluid.2018.12.007](https://doi.org/10.1016/j.fluid.2018.12.007)
