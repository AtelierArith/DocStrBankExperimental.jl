```
dranks(x, nbins)
```

0..nbinsでスケーリングされたランクを計算します。

# 引数

  * `x::AbstractArray`: 反応時間（応答を示すのにかかる時間）などの連続変数
  * `nbins::Int64`: ビンの数、デフォルトはスタージェスの公式（`nbins = 1 + log2(length(x)))`）

# 戻り値

  * `sr::Array{Int64}`
