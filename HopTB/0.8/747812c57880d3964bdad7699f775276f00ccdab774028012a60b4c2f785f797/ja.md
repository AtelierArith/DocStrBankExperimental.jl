```julia
get_berry_curvature(tm::AbstractTBModel, α::Int64, β::Int64, k::Vector{<:Real})::Vector{Float64}
```

`tm`における`k`でのベリー曲率Ωを計算します。

Ω[n]は、バンドnが非縮退または完全に縮退している場合にのみ正しいです。
