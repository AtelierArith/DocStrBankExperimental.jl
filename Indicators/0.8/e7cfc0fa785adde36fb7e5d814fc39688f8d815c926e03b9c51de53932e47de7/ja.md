```
donch(hl::Matrix{T}; n::Int64=10, inclusive::Bool=true)::Array{Float64}
```

ドンチャンチャネル（inclusiveがtrueに設定されている場合、計算に現在のバーを含めます。）

*出力*

  * 列1: 最後の `n` 期間の最低安値
  * 列2: 最後の `n` 期間の最高高値と最低安値の平均
  * 列3: 最後の `n` 期間の最高高値
