```
normscale(flat::ModulatedFourierLattice, expon::Real, 
          Gs::Union{ReciprocalBasis, Nothing} = nothing)  --> ModulatedFourierLattice
```

Applies inverse-orbit norm rescaling of expansion coefficients with a norm exponent `expon`. If `Gs` is nothing, the orbit norm is computed in the lattice basis (and, so, is not strictly a norm); by providing `Gs` as [`ReciprocalBasis`](@ref), the norm is evaluated correctly in cartesian setting. See further discussion in [`modulate`](@ref).

An in-place equivalent is provided in [`normscale!`](@ref).
