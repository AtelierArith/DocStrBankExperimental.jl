```
XiangDeiters::SingleFluid
XiangDeiters(component;
    idealmodel = BasicIdeal,
    userlocations = String[],
    ideal_userlocations = String[],
    Rgas = nothing,
    verbose = false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m3/mol]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `acentricfactor`: 単一パラメータ (`Float64`)

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

Xiang-Deitersモデルは、臨界値とアセントリック因子から単一成分の経験的EoSモデルを推定します。

```
Zc = PcVc/RTc
θ = (Zc - 0.29)^2
aᵣ = a₀(δ,τ) + ω*a₁(δ,τ) + θ*a₂(δ,τ)
```

`Rgas`は、プロパティ計算中に使用される気体定数の値を設定するために使用できます。

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = XiangDeiters("water") #単一入力
model = XiangDeiters(["water"]) #ベクトルとしての単一入力
model = XiangDeiters(["water"], idealmodel = ReidIdeal) #理想モデルの変更

# 事前構築されたモデルを渡す

my_idealmodel = MonomerIdeal(["ethane"])
model = XiangDeiters(["ethane"],idealmodel = my_idealmodel)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = XiangDeiters(["hydrogen"]; userlocations = ["path/to/my/db","critical.csv"]);

# ユーザー提供のパラメータ、パラメータを直接渡す

model = XiangDeiters(["hydrogen"];
        userlocations = (;Tc = [44.492],
                        Pc = [2679000],
                        Vc = [4.25e-5],
                        Mw = [2.0],
                        acentricfactor = [-0.21])
                    )
```

## 参考文献

1. Xiang, H. W., & Deiters, U. K. (2008). A new generalized corresponding-states equation of state for the extension of the Lee–Kesler equation to fluids consisting of polar and larger nonpolar molecules. Chemical Engineering Science, 63(6), 1490–1496. [doi:10.1016/j.ces.2007.11.029](https://doi.org/10.1016/j.ces.2007.11.029)
