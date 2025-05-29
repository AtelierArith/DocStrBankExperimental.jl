```
UNIQUACModel <: ActivityModel

UNIQUAC(components;
puremodel = PR,
userlocations = String[], 
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `a`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリ相互作用エネルギーパラメータ
  * `r`: 単一パラメータ (`Float64`)  - 正規化されたファンデルワールス体積
  * `q`: 単一パラメータ (`Float64`) - 正規化された表面積
  * `q_p`: 単一パラメータ (`Float64`) - 修正された正規化表面積
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

UNIQUAC (Universal QuasiChemical Activity Coefficients) 活動モデル:

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res))
gᴱ(comb) = ∑[xᵢlog(Φᵢ/xᵢ) + 5qᵢxᵢlog(θᵢ/Φᵢ)]
gᴱ(res) = -∑xᵢqᵖᵢlog(∑θᵖⱼτⱼᵢ)
θᵢ = qᵢxᵢ/∑qᵢxᵢ
θᵖ = qᵖᵢxᵢ/∑qᵖᵢxᵢ
Φᵢ = rᵢxᵢ/∑rᵢxᵢ
τᵢⱼ = exp(-aᵢⱼ/T)
```

## モデル構築の例

```
# デフォルトデータベースを使用
model = UNIQUAC(["water","ethanol"]) #デフォルトの純粋モデル: PR
model = UNIQUAC(["water","ethanol"],puremodel = BasicIdeal) #純粋モデル特性に理想気体を使用
model = UNIQUAC(["water","ethanol"],puremodel = PCSAFT) #純粋モデル特性に実気体モデルを使用

# 事前構築されたモデルを渡す

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = UNIQUAC(["water","ethanol"],puremodel = my_puremodel)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
model = UNIQUAC(["water","ethanol"];userlocations = ["path/to/my/db","uniquac_ge.csv"])

# パラメータを直接渡す
model = UNIQUAC(["water","ethanol"],
        userlocations = (a = [0.0 378.1; 258.4 0.0], 
                        r = [0.92, 2.11],
                        q = [1.4, 1.97],
                        q_p = [1.0, 0.92],
                        Mw = [18.015, 46.069])
                    )
```

## 参考文献

1. Abrams, D. S., & Prausnitz, J. M. (1975). 液体混合物の統計熱力学: 部分的または完全に混和可能な系の過剰ギブズエネルギーの新しい表現. AIChEジャーナル. アメリカ化学工学協会, 21(1), 116–128. [doi:10.1002/aic.690210115](https://doi.org/10.1002/aic.690210115)
