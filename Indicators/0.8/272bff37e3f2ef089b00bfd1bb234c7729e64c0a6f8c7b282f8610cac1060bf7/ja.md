```
macd(x::Array{T}; nfast::Int64=12, nslow::Int64=26, nsig::Int64=9)::Array{Float64}
```

移動平均収束発散

*出力*

  * 列 1: MACD
  * 列 2: MACD シグナルライン
  * 列 3: MACD ヒストグラム
