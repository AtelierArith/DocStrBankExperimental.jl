```
COSTALD(components; 
            userlocations::Vector{String}=String[], 
            verbose::Bool=false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (Float64) - 臨界温度 `[K]`
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m³/mol]`
  * `acentricfactor`: 単一パラメータ (`Float64`) - アセントリック因子

## 説明

COSTALD状態方程式は飽和液体のためのものであり、圧力には依存しません。

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = COSTALD("water") #単一入力
model = COSTALD(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = COSTALD(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = COSTALD(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Vc = [4.25e-5, 6.43e-5],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## 参考文献

Hankinson, R. W., & Thomson, G. H. (1979). A new correlation for saturated densities of liquids and their mixtures. AIChE Journal. American Institute of Chemical Engineers, 25(4), 653–663. [doi:10.1002/aic.690250412](https://doi.org/doi:10.1002/aic.690250412)
