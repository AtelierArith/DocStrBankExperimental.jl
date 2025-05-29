```
update_forgetful_mv(x::AbstractVector{T}, V̄ₜ::T, x̄ₜ::T, c::E) where {T<:Number, E<:AbstractFloat}
```

Given the previous value of the forgetful variance `V̄ₜ` and foregetul mean `x̄ₜ`, calculate their updated values `V̄ₜ₊₁` and `x̄ₜ₊₁`, assuming that `x[end] = xₜ₊₁` has already been appended to `x`. The oldest `c` fraction of values is discarded when calculating the forgetful mean and variance.
