```
AbbottVirial <: SecondVirialModel
AbbottVirial(components;
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
B₀ = 0.083 + 0.422/Trᵢⱼ^1.6
B₁ = 0.139 - 0.172/Trᵢⱼ^4.2
Trᵢⱼ = T/Tcᵢⱼ
Tcᵢⱼ = √TcᵢTcⱼ
Pcᵢⱼ = (Pcᵢ + Pcⱼ)/2
ωᵢⱼ = (ωᵢ + ωⱼ)/2
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = AbbottVirial("water") #単一入力
model = AbbottVirial(["water","ethanol"]) #複数成分
model = AbbottVirial(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更

# 事前構築されたモデルを渡す

my_idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
model = AbbottVirial(["neon","hydrogen"],idealmodel = my_idealmodel)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = AbbottVirial(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = AbbottVirial(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## 参考文献

1. Smith, H. C. Van Ness Joseph M. Introduction to Chemical Engineering Thermodynamics 4E 1987.
