```
InterpolatedProfiles(M::AbstractVector{<:AbstractMatrix}, Interp::Type{<:AbstractInterpolation}=QuadraticInterpolation) -> Vector{Function}
```

Interpolates the `Vector{Matrix}` output of `ParameterProfiles`. !!!note     Does not distinguish between converged and non-converged points in the profile.
