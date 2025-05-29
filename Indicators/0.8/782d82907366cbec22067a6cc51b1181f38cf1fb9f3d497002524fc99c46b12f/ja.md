```
runmax(x::Vector{T}; n::Int=10, cumulative::Bool=true, inclusive::Bool=true)::Vector{Float64}
runmax(X::Matrix; n::Int=10, cumulative::Bool=true, inclusive::Bool=true)::Matrix{Float64}
```

配列のランニングまたはローリング最大値を計算します
