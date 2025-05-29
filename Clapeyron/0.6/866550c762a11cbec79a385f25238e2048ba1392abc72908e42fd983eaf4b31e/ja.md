```
TsonopoulosVirial <: SecondVirialModel
TsonopoulosVirial(components;
        idealmodel = BasicIdeal,
        userlocations = String[],
        ideal_userlocations = String[],
        verbose = false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `acentricfactor`: 単一パラメータ (`Float64`) - アセントリック因子
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

対応状態原理を用いたビリアルモデル：

```
B = ∑xᵢxⱼBᵢⱼ
Bᵢⱼ = BrᵢⱼRTcᵢⱼ/Pcᵢⱼ
Brᵢⱼ = B₀ + ωᵢⱼB₁
B₀ = 0.1445 - 0.330/Trᵢⱼ - 0.1385/Trᵢⱼ^2 - 0.0121/Trᵢⱼ^3 - 0.000607/Trᵢⱼ^8
B₁ = 0.0637 + 0.331/Trᵢⱼ - 0.423/Trᵢⱼ^2 - 0.423/Trᵢⱼ^3 - 0.008/Trᵢⱼ^8
Trᵢⱼ = T/Tcᵢⱼ
Tcᵢⱼ = √TcᵢTcⱼ
Pcᵢⱼ = (Pcᵢ + Pcⱼ)/2
ωᵢⱼ = (ωᵢ + ωⱼ)/2
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = TsonopoulosVirial("water") #単一入力
model = TsonopoulosVirial(["water","ethanol"]) #複数成分
model = TsonopoulosVirial(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更

# 事前構築されたモデルを渡す

my_idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
model = TsonopoulosVirial(["neon","hydrogen"],idealmodel = my_idealmodel)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = TsonopoulosVirial(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = TsonopoulosVirial(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## 参考文献

1. Tsonopoulos, C. (1974). An empirical correlation of second virial coefficients. AIChE Journal. American Institute of Chemical Engineers, 20(2), 263–272. [doi:10.1002/aic.690200209](https://doi.org/10.1002/aic.690200209)
