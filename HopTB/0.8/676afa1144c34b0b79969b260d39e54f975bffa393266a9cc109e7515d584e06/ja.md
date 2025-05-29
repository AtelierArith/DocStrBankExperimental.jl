```julia
getH(tm::AbstractTBModel, k::AbstractVector{<:Real})::Matrix{ComplexF64}
```

縮小された `k` 点でハミルトニアンを計算します。
