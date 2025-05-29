```
LeeKeslerSat <: SaturationModel

LeeKeslerSat(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `acentricfactor`: 単一パラメータ (`Float64`) - アセントリック因子

## 説明

飽和圧力のためのリー・ケスラー相関:

```
psat(T) = f₀ + ω•f₁
Tr = T/Tc
f₀ = 5.92714 - 6.09648/Tr - 1.28862•log(Tr) + 0.169347•Tr⁶
f₁ = 15.2518 - 15.6875/Tr - 13.4721•log(Tr) + 0.43577•Tr⁶
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
sat = LeeKeslerSat("water") #単一入力
sat = LeeKeslerSat(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
sat = LeeKeslerSat(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

sat = LeeKeslerSat(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## 参考文献

1. Lee, B. I., & Kesler, M. G. (1975). A generalized thermodynamic correlation based on three-parameter corresponding states. AIChE journal. American Institute of Chemical Engineers, 21(3), 510–527. [doi:10.1002/aic.690210313](https://doi.org/10.1002/aic.690210313)
