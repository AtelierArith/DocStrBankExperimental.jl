```
heikinashi(ohlc::AbstractMatrix{<:Real})::Matrix{Float64}
```

平滑足

*出力*

  * 列 1: 平滑足の始値 – 前回の (o+c)/2
  * 列 2: 平滑足の高値 – max(o,h)
  * 列 3: 平滑足の安値 – min(o,l)
  * 列 4: 平滑足の終値 – (o+h+l+c)/4
