```
Wilson <: ActivityModel
Wilson(components;
puremodel = PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `acentricfactor`: 単一パラメータ (`Float64`) - アセントリック因子
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `g`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ

## モデルパラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `ZRA`: 単一パラメータ (`Float64`) - Rackett圧縮性因子
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `g`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

Wilson活動モデル、液体体積のRackett相関を用いる：

```
Gᴱ = nRT∑xᵢlog(∑xⱼjΛᵢⱼ)
Λᵢⱼ = exp(-gᵢⱼ/T)*Vⱼ/Vᵢ
ZRAᵢ = 0.29056 - 0.08775ωᵢ
Vᵢ = (RTcᵢ/Pcᵢ)ZRAᵢ^(1 + (1-T/Tcᵢ)^2/7)
```

## モデル構築の例

```
# デフォルトデータベースを使用
model = Wilson(["water","ethanol"]) #デフォルトの純粋モデル: PR
model = Wilson(["water","ethanol"],puremodel = BasicIdeal) #純粋モデル特性に理想気体を使用
model = Wilson(["water","ethanol"],puremodel = PCSAFT) #純粋モデル特性に実気体モデルを使用

# 事前構築されたモデルを渡す

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = Wilson(["water","ethanol"],puremodel = my_puremodel)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
model = Wilson(["water","ethanol"];userlocations = ["path/to/my/db","wilson.csv"])

# パラメータを直接渡す
model = Wilson(["water","ethanol"],
        userlocations = (g = [0.0 3988.52; 1360.117 0.0],
                        Tc = [647.13, 513.92],
                        Pc = [2.19e7, 6.12e6],
                        acentricfactor = [0.343, 0.643],
                        Mw = [18.015, 46.069])
                        )
```

## 参考文献

1. Wilson, G. M. (1964). Vapor-liquid equilibrium. XI. A new expression for the excess free energy of mixing. Journal of the American Chemical Society, 86(2), 127–130. [doi:10.1021/ja01056a002](https://doi.org/10.1021/ja01056a002)
