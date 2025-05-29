```julia
getdS(tm::AbstractTBModel, order::Tuple{Int64,Int64,Int64},
    k::AbstractVector{<:Real})::Matrix{ComplexF64}
```

重なりの`order`導関数を計算します。
