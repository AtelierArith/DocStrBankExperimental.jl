```julia
getdH(tm::AbstractTBModel, order::Tuple{Int64,Int64,Int64},
    k::AbstractVector{<:Real})::Matrix{ComplexF64}
```

ハミルトニアンの`order`階の導関数を計算します。
