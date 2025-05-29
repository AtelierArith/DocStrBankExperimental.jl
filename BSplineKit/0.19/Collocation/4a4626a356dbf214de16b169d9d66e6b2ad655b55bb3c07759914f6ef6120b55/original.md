```
collocation_matrix!(
    C::AbstractMatrix{T}, B::AbstractBSplineBasis, x::AbstractVector,
    [deriv::Derivative = Derivative(0)]; clip_threshold = eps(T))
```

Fill preallocated collocation matrix.

See [`collocation_matrix`](@ref) for details.
