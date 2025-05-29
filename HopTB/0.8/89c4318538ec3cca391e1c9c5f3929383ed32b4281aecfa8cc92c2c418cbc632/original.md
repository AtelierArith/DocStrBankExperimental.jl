```julia
getvelocity(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Number})
```

Calculate velocity matrix in the α direction.

Velocity matrix is calculated by the following expression

$$
v_{nm}^α = ∂_α ϵ_n δ_{nm} + i (ϵ_n-ϵ_m) A_{nm}^α.
$$

Therefore, the velocity is actually ħ*velocity.

v[n, m] is only correct when band m is nondegenerate or completely degenerate.
