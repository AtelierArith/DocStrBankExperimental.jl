```
runmad(x::Vector{T}; n::Int=10, cumulative::Bool=true, fun::Function=median)::Vector{Float64}
runmad(X::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

配列の移動またはロール平均絶対偏差を計算します。
