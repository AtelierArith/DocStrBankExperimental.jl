```
runmin(x::Vector{T}; n::Int=10, cumulative::Bool=true, inclusive::Bool=true)::Vector{Float64}
runmin(X::Matrix; n::Int=10, cumulative::Bool=true, inclusive::Bool=true)::Matrix{Float64}
```

配列のランニングまたはローリング最小値を計算します
