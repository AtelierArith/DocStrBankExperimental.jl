```julia
ExponentialScheduling(alpha::Float64; iter::Int64, max_iter::Int64, rate::Float64 = 1.0) --> Float64
```

イテレーション `iter` に対して、いくつかのレート `rate` で指数的に減少したアルファ値を返します。
