```julia
predictVariableByFactor(dfg, targetsym, fct, prevars)

```

変数の現在の推定値と予測値を比較するためのメソッドで、新しい因子を因子グラフに追加する前にテストするために開発されました。

ノート

  * `fct` は因子グラフに含まれている必要はありません - 事前にテストするために使用される可能性があります。
  * この関数は `multihypo` を使用すべきかどうかを検出するのに役立ちます。
  * `approxConv` は、いくつかの因子を通じて完全な信念推定を投影しますが、すでに因子グラフに存在している必要があります。

例

```julia
# fg はすでに :x7 と :l3 を含んでいます
pp = Pose2Point2BearingRange(Normal(0,0.1),Normal(10,1.0))
# :x7 から :l3 への新しい測定値の可能性
curr, pred = predictVariableByFactor(fg, :l3, pp, [:x7; :l3])
# フィットスコアに対する素朴なユーザー定義テストの例
fitscore = minkld(curr, pred)
# `multihypo` は既存の変数と新しい変数の間のオプションとして使用できます
```

関連

approxConv
