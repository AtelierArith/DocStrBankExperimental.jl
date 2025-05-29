```
NRTL <: ActivityModel

function NRTL(components;
puremodel=PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `a`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `b`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `c`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `Mw`: 単一パラメータ (`Float64`) (オプション) - 分子量 `[g/mol]`

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

NRTL (Non Random Two Fluid) 活動モデル:

```
Gᴱ = nRT∑[xᵢ(∑τⱼᵢGⱼᵢxⱼ)/(∑Gⱼᵢxⱼ)]
Gᵢⱼ exp(-cᵢⱼτᵢⱼ)
τᵢⱼ = aᵢⱼ + bᵢⱼ/T
```

## モデル構築の例

```
# デフォルトのデータベースを使用
model = NRTL(["water","ethanol"]) #デフォルトの純粋モデル: PR
model = NRTL(["water","ethanol"],puremodel = BasicIdeal) #純粋モデル特性に理想気体を使用
model = NRTL(["water","ethanol"],puremodel = PCSAFT) #純粋モデル特性に実気体モデルを使用

# 事前構築されたモデルを渡す

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = NRTL(["water","ethanol"],puremodel = my_puremodel)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
model = NRTL(["water","ethanol"];userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
model = NRTL(["water","ethanol"],
userlocations = (a = [0.0 3.458; -0.801 0.0],
                b = [0.0 -586.1; 246.2 0.0],
                c = [0.0 0.3; 0.3 0.0])
            )
```

## 参考文献

1. Renon, H., & Prausnitz, J. M. (1968). Local compositions in thermodynamic excess functions for liquid mixtures. AIChE journal. American Institute of Chemical Engineers, 14(1), 135–144. [doi:10.1002/aic.690140124](https://doi.org/10.1002/aic.690140124)
