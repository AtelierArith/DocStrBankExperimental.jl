```
LKPmod <: LKPModel
LKPmod(components;
    idealmodel=BasicIdeal,
    verbose=false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Vc`: 単一パラメータ (`Float64`) (オプション) - 臨界体積 `[m^3]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `acentricfactor`: 単一パラメータ (`Float64`) - アセントリックファクター（単位なし）
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ（単位なし）

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

リー・ケスラー・プローカー状態方程式。単純な球状流体（メタン、`∅`）と参照流体（n-オクタン、`ref`）の間の補間を使用した対応状態：

元のEoSの係数は、液相におけるEoSの正しい挙動を保証するために[2]で修正されました。

```
αᵣ = (1 - ωᵣ)*αᵣ(δr,τ,params(∅)) + ωᵣ*αᵣ(δr,τ,params(ref))
τ = Tr/T
δr = Vr/V/Zr
Zr = Pr*Vr/(R*Tr)
Pr = (0.2905 - 0.085*ω̄)*R*Tr/Vr
ωᵣ = (ω̄ - ω(∅))/(ω(ref) - ω(∅))
ω̄ = ∑xᵢωᵢ
Tr = ∑xᵢ*xⱼ*Tcᵢⱼ*Vcᵢⱼ^η * (1-kᵢⱼ)
Vr = ∑xᵢ*xⱼ*Tcᵢⱼ*Vcᵢⱼ
Tcᵢⱼ = √Tcᵢ*Tcⱼ
Vcᵢⱼ = 0.125*(∛Vcᵢ + ∛Vcⱼ)^3
η = 0.25
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = LKPmod("water") #単一入力
model = LKPmod(["water","ethanol"]) #複数成分
model = LKPmod(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの修正

# 事前構築されたモデルを渡す

my_idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
model =  LKPmod(["neon","hydrogen"],idealmodel = my_idealmodel)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = LKPmod(["neon","hydrogen"]; userlocations = ["path/to/my/db","lkp/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = LKPmod(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Vc = [4.25e-5, 6.43e-5],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.]) #k,lは単一成分モデルでは省略可能。
                    )
```

## 参考文献

1. Plöcker, U., Knapp, H., & Prausnitz, J. (1978). Calculation of high-pressure vapor-liquid equilibria from a corresponding-states correlation with emphasis on asymmetric mixtures. Industrial & Engineering Chemistry Process Design and Development, 17(3), 324–332. [doi:10.1021/i260067a020](https://doi.org/10.1021/i260067a020)
2. Sabozin, F., Jäger, A., & Thol, M. (2024). Enhancement of the Lee–Kesler–Plöcker equation of state for calculating thermodynamic properties of long-chain alkanes. International Journal of Thermophysics, 45(5). [doi:10.1007/s10765-024-03360-0](https://doi.org/10.1007/s10765-024-03360-0)
