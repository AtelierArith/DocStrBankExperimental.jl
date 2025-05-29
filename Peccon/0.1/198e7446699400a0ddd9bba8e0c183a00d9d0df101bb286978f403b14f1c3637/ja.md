```
data_alpha(Tickers)
```

は、alphavantageから複数の株の毎日の価格情報を抽出し、それらをデータフレームのベクターに格納します。

# 例

```julia-repl
julia> data_alpha(["ADAEUR", "SPY"])
```
