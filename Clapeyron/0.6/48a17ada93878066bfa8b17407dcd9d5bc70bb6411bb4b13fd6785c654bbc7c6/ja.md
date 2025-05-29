```
AlyLeeIdeal <: AlyLeeIdealModel

AlyLeeIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

  * `A`: 単一パラメータ (`Float64`) - モデル係数
  * `B`: 単一パラメータ (`Float64`) - モデル係数
  * `C`: 単一パラメータ (`Float64`) - モデル係数
  * `D`: 単一パラメータ (`Float64`) - モデル係数
  * `E`: 単一パラメータ (`Float64`) - モデル係数
  * `F`: 単一パラメータ (`Float64`) - モデル係数
  * `G`: 単一パラメータ (`Float64`) - モデル係数
  * `H`: 単一パラメータ (`Float64`) - モデル係数
  * `I`: 単一パラメータ (`Float64`) - モデル係数
  * `Mw`: 単一パラメータ (`Float64`) (オプション) - 分子量 `[g/mol]`

## 説明

Aly-Lee理想モデル（拡張）:

```
Cpᵢ(T)/R = A + B(CT⁻¹/sinh(CT⁻¹))² + D(ET⁻¹/cosh(ET⁻¹))² + F(GT⁻¹/sinh(GT⁻¹))² + H(IT⁻¹/cosh(IT⁻¹))²
```

## モデル構築の例

```
# デフォルトデータベースを使用
idealmodel = AlyLeeIdeal("water") #単一入力
idealmodel = AlyLeeIdeal(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
idealmodel = AlyLeeIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","alylee.csv"])

# パラメータを直接渡す
idealmodel = AlyLeeIdeal(["water","carbon dioxide"];
                        userlocations = (A = [4.004, 3.5],
                        B = [0.01, 2.044],
                        C = [268.8, 919.3],
                        D = [0.99, -1.06],
                        E = [1141.4, -865.1],
                        F = [3.07, 2.034],
                        G = [2507.37, 483.55],
                        H = [0.0, 0.0139],
                        I = [0.0, 341.11])
                        )
```

## 参考文献

1. Aly, F. A., & Lee, L. L. (1981). 自己整合方程式による理想気体の比熱、エンタルピー、およびエントロピーの計算。流体相平衡, 6(3–4), 169–179. [doi:10.1016/0378-3812(81)85002-9](https://doi.org/10.1016/0378-3812(81)85002-9)
