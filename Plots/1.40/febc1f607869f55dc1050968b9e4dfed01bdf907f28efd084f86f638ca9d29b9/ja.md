```
ohlc(x,y::Vector{OHLC})
ohlc!(x,y::Vector{OHLC})
```

オープン・ハイ・ロー・クローズプロットを作成します。yの各エントリは、ロー値からハイ値まで延びる垂直セグメントで表され、左側と右側にはそれぞれオープン値とクローズ値を示す短い水平セグメントがあります。

# 例

```julia-repl
julia> meanprices = cumsum(randn(100))
julia> y = OHLC[(p+rand(),p+1,p-1,p+rand()) for p in meanprices]
julia> ohlc(y)
```
