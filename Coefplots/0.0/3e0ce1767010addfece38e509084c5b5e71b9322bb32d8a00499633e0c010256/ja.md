```
バー
```

これは `Coefplot.errbar`、`Coefplot.connect`、および `Multi-`、`Grouoped-`、`GroupedMultiCoefplot` に入ります。

# コンストラクタ

```julia
Bar(;draw=missing, linewidth=missing, linetype=missing)
```

# キーワード引数

  * `draw::Union{Color, Missing}` はバーの色です。
  * `linetype::Union{Real, Missing}` はバーを描画するために使用される線のタイプです。利用可能な選択肢は次のとおりです: `"solid"`、`"dotted"`、`"densely dotted"`、`"loosely dotted"`、`"dashed"`、`"densely dashed"`、`"loosely dashed"`、`"dash dot"`、`"densely dash dot"`、`"loosely dash dot"`、`"dash dot dot"`、`"densely dash dot dot"`、`"loosely dash dot dot"`。
  * `linewidth::Union{Real, Missing}` はバーを描画するために使用される線の幅です。
