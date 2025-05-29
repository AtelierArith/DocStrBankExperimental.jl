```
aspenNRTL <: ActivityModel

function aspenNRTL(components;
puremodel=PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `a0`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `a1`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `t0`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `t1`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `t2`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `t3`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

NRTL (Non Random Two Fluid) 活動モデル:

```
Gᴱ = nRT∑[xᵢ(∑τⱼᵢGⱼᵢxⱼ)/(∑Gⱼᵢxⱼ)]
Gᵢⱼ exp(-αᵢⱼτᵢⱼ)
αᵢⱼ = αᵢⱼ₀ + αᵢⱼ₁T
τᵢⱼ = tᵢⱼ₀ + tᵢⱼ₁/T + tᵢⱼ₂*ln(T) + tᵢⱼ₃*T
```

## モデル構築の例

```
# デフォルトのデータベースを使用
model = aspenNRTL(["water","ethanol"]) #デフォルトの純粋モデル: PR
model = aspenNRTL(["water","ethanol"],puremodel = BasicIdeal) #純粋モデル特性に理想気体を使用
model = aspenNRTL(["water","ethanol"],puremodel = PCSAFT) #純粋モデル特性に実気体モデルを使用
# 事前構築されたモデルを渡す

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = aspenNRTL(["water","ethanol"],puremodel = my_puremodel)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
model = aspenNRTL(["water","ethanol"];userlocations = ["path/to/my/db","nrtl.csv"])

# パラメータを直接渡す
model = aspenNRTL(["water","acetone"],
userlocations = (a0 = [0.0 0.228632; 0.228632 0.0],
                a1 = [0.0 0.000136; 0.000136 0.0],
                t0 = [0.0 13.374756; 16.081848 0.0],
                t1 = [0.0 -415.527344; -88.8125 0.0],
                t2 = [0.0 -1.913689; -2.930901 0.0],
                t3 = [0.0 0.00153; 0.005305 0.0])
            )
```

## 参考文献

1. Renon, H., & Prausnitz, J. M. (1968). 液体混合物の熱力学的過剰関数における局所組成. AIChEジャーナル. アメリカ化学工学会, 14(1), 135–144. [doi:10.1002/aic.690140124](https://doi.org/10.1002/aic.690140124)

```
