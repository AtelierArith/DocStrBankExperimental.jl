パッケージ: ForecastPlots

```
dplot(x; dlabels = ["Data","Trend","Seasonal","Remainder"])
```

時系列の季節性、トレンド、残差の分解をプロットします。

# 引数

  * `x`: 季節性、トレンド、残差の分解を含む3列の行列
  * `dlabels`: データ、季節性、トレンド、残差のラベルを含む長さ4の文字列配列。

# 戻り値

スケールバー付きの季節分解プロット

# 例

```julia-repl
dplot(randn(100,3))
dplot(randn(100,3); labels = ["データ","トレンド","季節性","残差"])
dplot(rand(100,3),now()-Day(99):Day(1):now())
```
