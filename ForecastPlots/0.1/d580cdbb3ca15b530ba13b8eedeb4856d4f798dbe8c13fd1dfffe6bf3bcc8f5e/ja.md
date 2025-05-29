パッケージ: ForecastPlots

```
candel(x, t, args...; colors = (:green, :red), kw...)
```

株価のローソク足をプロットします

# 引数

  * `x`: 始値、高値、安値、終値の値を持つ4列の行列。
  * `t`: 時間単位のベクトルで、デフォルトは1:size(x,1)
  * `args...`: `plot` 引数
  * `colors`: 上昇と下降の色シンボルのタプルで、デフォルトは (:green,:red)
  * `kw...`: `plot` キーワード引数

# 戻り値

ローソク足プロット

# 例

```julia-repl
using MarketData

x = yahoo(:INTC)
last_month_intc = values(x)[end-30:end,1:4]
candle(last_month_intc)
candle(last_month_intc,timestamp(x)[end-30:end])
candle(last_month_intc,timestamp(x)[end-30:end]; colors=(:white,:black), title = "INTC")
```
