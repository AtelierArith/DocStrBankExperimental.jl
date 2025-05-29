```
RegularSpacing{T<:Real} <: AbstractVector{T}
```

`RegularSpacing(t0, Δt, N)` represents the same thing as `range(t0; step=Δt, length=N)`, but has a different implementation which avoids using extended-precision floating point numbers. This is needed for all AD frameworks.
