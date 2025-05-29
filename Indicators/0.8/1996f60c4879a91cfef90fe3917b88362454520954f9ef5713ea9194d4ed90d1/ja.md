```
runcor(x::Vector{T}, y::Vector{T}; n::Int=10, cumulative::Bool=true)::Vector{Float64}
runcor(X::Matrix, y::Vector; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
runcor(X::Matrix, Y::Matrix; n::Int=10, cumulative::Bool=true)::Matrix{Float64}
```

二つの配列の移動相関またはロール相関を計算します。
