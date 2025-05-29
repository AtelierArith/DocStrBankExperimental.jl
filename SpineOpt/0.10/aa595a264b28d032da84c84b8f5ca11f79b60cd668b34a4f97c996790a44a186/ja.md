```
time_slice(m; temporal_block=anything, t=anything)
```

モデル `m` の `TimeSlice` の `Array`。

# 引数

  * `temporal_block::Union{Object,Vector{Object}}`: これらのブロック内の `TimeSlice` のみを返します。
  * `t::Union{TimeSlice,Vector{TimeSlice}}`: このコレクションにも含まれる `TimeSlice` のみを返します。
