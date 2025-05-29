```
PPDSIdeal <: PPDSIdealModel

PPDSIdeal(components;
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
  * `Mw`: 単一パラメータ (`Float64`) (オプション) - 分子量 `[g/mol]`

## 説明

PPDS理想モデル:

```
Cpᵢ(T)/R = B + (C - B)y²[1 + (y − 1)(D + Ey + Fy² + Gy³)]
y = T/(A + T)
```

## モデル構築の例

```
# デフォルトデータベースを使用
idealmodel = PPDSIdeal("water") #単一入力
idealmodel = PPDSIdeal(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
idealmodel = PPDSIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","alylee.csv"])

# パラメータを直接渡す
idealmodel = PPDSIdeal(["water","carbon dioxide"];
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

1. Gmehling, J., Kleiber, M., Kolbe, B., & Rarey, J. (2019). Chemical thermodynamics for process simulation (2nd ed.). Berlin, Germany: Blackwell Verlag.
