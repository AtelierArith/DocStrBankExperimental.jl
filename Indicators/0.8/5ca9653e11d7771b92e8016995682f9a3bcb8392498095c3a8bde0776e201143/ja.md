```
runsum(x::Vector{T}; n::Int=10, cumulative::Bool=true)::Vector{Float64}
runsum(X::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

配列の累積またはロール合計を計算します。
