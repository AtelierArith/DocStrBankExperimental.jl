```
tcPRWilsonRes <: WilsonModel
tcPRWilsonRes(components;
puremodel = BasicIdeal,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `g`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - 相互作用パラメータ
  * `v`: 単一パラメータ（オプション） (`Float64`) - 個々の体積。

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

tc-PR-Wilson残差活性モデルは、tc-PR立方体EoSと組み合わせて使用することを目的としています：

```
Gᴱᵣ = nRT( ∑xᵢlog(∑xⱼjΛᵢⱼ) - ∑xᵢ*(log(vᵢ/v) )
Λᵢⱼ = exp(-gᵢⱼ/T)*Vⱼ/Vᵢ 
```

## モデル構築の例

```
# デフォルトデータベースを使用
model = tcPRWilsonRes(["water","ethanol"]) #デフォルトの純粋モデル: PR
model = tcPRWilsonRes(["water","ethanol"],puremodel = BasicIdeal) #純粋モデル特性のために理想気体を使用
model = tcPRWilsonRes(["water","ethanol"],puremodel = PCSAFT) #純粋モデル特性のために実気体モデルを使用

# 事前構築されたモデルを渡す

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = tcPRWilsonRes(["water","ethanol"],puremodel = my_puremodel)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
model = tcPRWilsonRes(["water","ethanol"];userlocations = ["path/to/my/db","tcpr_wilson.csv"])

# パラメータを直接渡す
model = tcPRWilsonRes(["water","ethanol"],userlocations = (;g = [0.0 3988.52; 1360.117 0.0]))
```

## 参考文献

1. Wilson, G. M. (1964). Vapor-liquid equilibrium. XI. A new expression for the excess free energy of mixing. Journal of the American Chemical Society, 86(2), 127–130. [doi:10.1021/ja01056a002](https://doi.org/10.1021/ja01056a002)
2. Piña-Martinez, A., Privat, R., Nikolaidis, I. K., Economou, I. G., & Jaubert, J.-N. (2021). What is the optimal activity coefficient model to be combined with the translated–consistent Peng–Robinson equation of state through advanced mixing rules? Cross-comparison and grading of the Wilson, UNIQUAC, and NRTL aE models against a benchmark database involving 200 binary systems. Industrial & Engineering Chemistry Research, 60(47), 17228–17247. [doi:10.1021/acs.iecr.1c03003](https://doi.org/10.1021/acs.iecr.1c03003)
