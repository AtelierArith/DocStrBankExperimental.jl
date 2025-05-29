```
runmean(x::Array{T}; n::Int=10, cumulative::Bool=true)::Array{T}
runmean(X::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

配列の移動またはロール算術平均を計算します。
