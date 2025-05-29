```
RackettLiquid(components;
userlocations::Vector{String}=String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (Float64) - 臨界温度 [K]
  * `Pc`: 単一パラメータ (Float64) - 臨界圧力 [Pa]
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m³/mol]`

## モデルパラメータ

  * `Tc`: 単一パラメータ (Float64) - 臨界温度 [K]
  * `Pc`: 単一パラメータ (Float64) - 臨界圧力 [Pa]
  * `Zc`: 単一パラメータ (Float64) - 臨界圧縮因子

## 説明

飽和液体のためのRackett状態方程式。圧力には依存しない。

```
Tr = T/Tc
V = (R̄Tc/Pc)Zc^(1+(1-Tr)^(2/7))
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = RackettLiquid("water") #単一入力
model = RackettLiquid(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = RackettLiquid(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = RackettLiquid(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Vc = [4.25e-5, 6.43e-5],
                        Pc = [2679000, 1296400])
                    )
```

## 参考文献

  * Rackett, H. G. (1970). 飽和液体のための状態方程式。Journal of Chemical and Engineering Data, 15(4), 514–517. [doi:10.1021/je60047a012](https://doi.org/10.1021/je60047a012)
