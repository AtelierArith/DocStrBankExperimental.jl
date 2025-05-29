```
normscale!(flat::ModulatedFourierLattice, expon::Real,
           Gs::Union{ReciprocalBasis, Nothing} = nothing) --> ModulatedFourierLattice
```

In-place equivalent of [`normscale`](@ref): mutates `flat`.
