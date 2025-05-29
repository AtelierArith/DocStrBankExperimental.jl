```
update_forgetful_mean(x::AbstractVector{T}, x̄ₜ::T, c::E) where {T<:Number, E<:AbstractFloat}
```

Given the previous value of the forgetful mean `x̄ₜ`, calculate its updated value `x̄ₜ₊₁` assuming that `x[end] = xₜ₊₁` has already been appended to `x`. The oldest `c` fraction of values is discarded when calculating the forgetful mean.
