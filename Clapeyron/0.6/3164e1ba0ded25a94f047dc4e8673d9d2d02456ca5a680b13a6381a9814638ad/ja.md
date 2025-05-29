```
JobackIdeal <: JobackIdealModel

JobackIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `N_a`: 単一パラメータ (`Float64`)
  * `T_c`: 単一パラメータ (`Float64`)
  * `P_c`: 単一パラメータ (`Float64`)
  * `V_c`: 単一パラメータ (`Float64`)
  * `T_b`: 単一パラメータ (`Float64`)
  * `T_m`: 単一パラメータ (`Float64`)
  * `H_form`: 単一パラメータ (`Float64`)
  * `G_form`: 単一パラメータ (`Float64`)
  * `a`: 単一パラメータ (`Float64`)
  * `b`: 単一パラメータ (`Float64`)
  * `c`: 単一パラメータ (`Float64`)
  * `d`: 単一パラメータ (`Float64`)
  * `H_fusion`: 単一パラメータ (`Float64`)
  * `H_vap`: 単一パラメータ (`Float64`)
  * `eta_a`: 単一パラメータ (`Float64`)
  * `eta_b`: 単一パラメータ (`Float64`)

## 説明

Jobackグループ寄与理想モデル。`ReidIdeal`のGCバージョン。ヘルムホルツエネルギーは比熱容量の積分を通じて得られます：

```
aᵢ = ∑(νᵢₖbₖ) - 37.93
bᵢ = ∑(νᵢₖbₖ) + 0.210
cᵢ = ∑(νᵢₖcₖ) - 3.91e-4
dᵢ = ∑(νᵢₖbₖ) + 2.06e-7
Cpᵢ(T) = aᵢ  + bᵢT + cᵢT^2 + dᵢT^3
```

GC平均Reidモデルは、`ReidIdeal(model::JobackIdeal)`を使用することで利用可能です。

単一成分の推定臨界点は、`crit_pure(model::JobackIdeal)`を通じて得られます。

## 参考文献

1. Joback, K. G., & Reid, R. C. (1987). Estimation of pure-component properties from group-contributions. Chemical Engineering Communications, 57(1–6), 233–243. [doi:10.1080/00986448708960487](https://doi.org/10.1080/00986448708960487)

## 利用可能なグループのリスト

|            名前 |         説明 |
| -------------:| ----------:|
|          -CH3 |        メチル |
|         -CH2- |       メチレン |
|          >CH- |            |
|           >C< |            |
|       CH2=CH- |            |
|       -CH=CH- |            |
|           =C< |            |
|           =C= |            |
|            CH |            |
|             C |            |
|     ring-CH2- |     環状アルカン |
|      ring>CH- |            |
|       ring>C< |            |
|      ring=CH- |    芳香族グループ |
|       ring=C< |            |
|            -F |       フッ化物 |
|           -Cl |        塩化物 |
|           -Br |        臭化物 |
|            -I |       ヨウ化物 |
|   -OH (アルコール) | ヒドロキシルグループ |
|   -OH (フェノール) |            |
|     -O- (非環状) |            |
|      -O- (環状) |            |
|    >C=O (非環状) |        ケトン |
|     >C=O (環状) |            |
| O=CH- (アルデヒド) |      アルデヒド |
|     -COOH (酸) |      カルボン酸 |
|  -COO- (エステル) |       エステル |
|      O (上記以外) |        ケトン |
|          -NH2 |        アミン |
|     >NH (非環状) |            |
|      >NH (環状) |            |
|     >N- (非環状) |            |
|     -N= (非環状) |            |
|      -N= (環状) |            |
|           =NH |            |
|           -CN |       ニトリル |
|          -NO3 |     ニトロキシル |
|           -SH |            |
|     -S- (非環状) |            |
|      -S- (環状) |            |
