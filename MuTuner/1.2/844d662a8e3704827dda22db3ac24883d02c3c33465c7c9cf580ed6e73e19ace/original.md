```
update_forgetful_var(x::AbstractVector{T}, V̄ₜ::T, x̄ₜ₊₁::T, x̄ₜ::T, c::E) where {T<:Number, E<:AbstractFloat}
```

Given the previous value for the forgetful variance `V̄ₜ` and foregetul mean `x̄ₜ`, and the updated value for the forgetful mean `x̄ₜ₊₁`, calculate the updated value `V̄ₜ₊₁`, assuming that `x[end] = xₜ₊₁` has already been appended to `x`. The oldest `c` fraction of values is discarded when calculating the forgetful variance.
