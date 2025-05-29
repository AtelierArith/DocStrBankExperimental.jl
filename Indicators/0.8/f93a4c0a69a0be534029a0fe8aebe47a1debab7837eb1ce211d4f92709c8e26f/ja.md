```
runquantile(x::Vector{T}; p::T=0.05, n::Int=10, cumulative::Bool=true)::Vector{Float64}
runquantile(X::Matrix; n::Int=10, cumulative::Bool=true, p::Real=0.05)::Matrix{Float64}
```

配列のランニング/ローリング分位数を計算します。
