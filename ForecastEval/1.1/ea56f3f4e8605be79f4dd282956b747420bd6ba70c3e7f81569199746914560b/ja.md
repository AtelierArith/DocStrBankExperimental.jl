```
MCSTest(inQF::Vector{Int}, outQF::Vector{Int}, pvalueQF::Vector{Float64}, inMT::Vector{Int}, outMT::Vector{Int}, pvalueMT::Vector{Float64})
```

Hansen, Lunde, Nason (2011) "The Model Confidence Set", Econometrica, 79 (2), pp. 453-497 で提案された MCS テストを実行した結果の出力タイプです。

このタイプのフィールド名は "QF" または "MT" で終わり、QF は二次形式テストに対応し（元の論文のセクション 3.1.1 を参照）、MT は最大 t 統計テストに対応します（元の論文のセクション 3.1.2 を参照）。

このタイプのフィールドでは、MCS メソッドに入力される予測モデルが、各予測モデルに対して 1 から始まる整数で示されています。これらの整数は、入力損失行列の列に対応します。詳細については ?mcs を参照してください。

このタイプのフィールドは次の通りです：

```
inQF <- 二次形式法による MCS に含まれるモデル
outQF <- 二次形式法による MCS に含まれないモデル
pvalueQF <- 二次形式法からの累積 p 値
inMT <- 最大 t 統計法による MCS に含まれるモデル
outMT <- 最大 t 統計法による MCS に含まれないモデル
pvalueMT <- 最大 t 統計法からの累積 p 値
```
