```julia
getvelocity(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Number})
```

α方向の速度行列を計算します。

速度行列は次の式によって計算されます。

$$
v_{nm}^α = ∂_α ϵ_n δ_{nm} + i (ϵ_n-ϵ_m) A_{nm}^α.
$$

したがって、速度は実際にはħ*速度です。

v[n, m]は、バンドmが非縮退または完全に縮退している場合にのみ正しいです。
