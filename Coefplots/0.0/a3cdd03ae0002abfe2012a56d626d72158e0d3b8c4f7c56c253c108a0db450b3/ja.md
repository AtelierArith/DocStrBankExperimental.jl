```
マーク
```

これは `Coefplot.mark`、`Coefplot.errormark`、および `Multi-`、`Grouoped-`、`GroupedMultiCoefplot` のものを入力します。

# コンストラクタ

```julia
Mark(;mark=missing, marksize=missing, linetype=missing, linewidth=missing, fill=missing, draw=missing)
```

# キーワード引数

  * `mark::Union{Symbol, String, Missing}` はマークの形状です。
  * `marksize::Union{Real, Missing}` はpt単位のマークのサイズです。
  * `linetype::Union{Real, Missing}` はマークのアウトラインの線の種類です。利用可能な選択肢は次のとおりです: `"solid"`、`"dotted"`、`"densely dotted"`、`"loosely dotted"`、`"dashed"`、`"densely dashed"`、`"loosely dashed"`、`"dash dot"`、`"densely dash dot"`、`"loosely dash dot"`、`"dash dot dot"`、`"densely dash dot dot"`、`"loosely dash dot dot"`。
  * `linewidth::Union{Real, Missing}` はマークのアウトラインの線の幅です。
  * `fill::Union{Color, Missing}` はマークを塗りつぶすために使用される色です。
  * `draw::Union{Color, Missing}` はマークのアウトラインを描くために使用される色です。
