```
YamadaGunnLiquid(components;
            userlocations::Vector{String}=String[],
            verbose::Bool=false)::RackettLiquid
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (Float64) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (Float64) - 臨界圧力 `[Pa]`
  * `acentricfactor`: 単一パラメータ (`Float64`) - アセントリック因子

## モデルパラメータ

  * `Tc`: 単一パラメータ (Float64) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (Float64) - 臨界圧力 `[Pa]`
  * `Zc`: 単一パラメータ (Float64) - 臨界圧縮因子

## 説明

Yamada-Gunn状態方程式は、圧縮因子 `Zc` を計算するために異なるアプローチを使用するRackett状態方程式の修正です：

```
Tr = T/Tc
Zc = 0.29056 - 0.08775ω
V = (R̄Tc/Pc)Zc^(1+(1-Tr)^(2/7))
```

`Vc` が不明な場合に `RackettLiquid` の代わりとして使用できます。

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = YamadaGunnLiquid("water") #単一入力
model = YamadaGunnLiquid(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = YamadaGunnLiquid(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = YamadaGunnLiquid(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## 参考文献

  * Rackett, H. G. (1970). Saturated liquidsの状態方程式. Journal of Chemical and Engineering Data, 15(4), 514–517. [doi:10.1021/je60047a012](https://doi.org/10.1021/je60047a012)
  * Gunn, R. D., & Yamada, T. (1971). Saturated liquid volumesの対応状態相関. AIChE Journal. American Institute of Chemical Engineers, 17(6), 1341–1345. [doi:10.1002/aic.690170613](https://doi.org/10.1002/aic.690170613)
