```julia
geteig(tm::AbstractTBModel, k::AbstractVector{<:Real})::HermEig
```

`tm`の縮小された`k`点での固有値と固有ベクトルを計算します。
