```
sum(A::Vector{MPS}; kwargs...)

sum(A::Vector{MPO}; kwargs...)
```

複数のMPS/MPOを互いに加算し、いくつかのオプションの切り捨てを行います。

# キーワード

  * `cutoff::Real`: 特異値切り捨てのカットオフ
  * `maxdim::Int`: 最大MPS/MPOボンド次元
