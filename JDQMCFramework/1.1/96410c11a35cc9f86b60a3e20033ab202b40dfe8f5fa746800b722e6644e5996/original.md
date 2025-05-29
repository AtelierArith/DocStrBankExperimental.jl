```
FermionGreensCalculator(
    B::AbstractVector{P},
    β::E, Δτ::E, n_stab::Int
) where {T<:Number, E<:AbstractFloat, P<:AbstractPropagator{T}}
```

Initialize and return [`FermionGreensCalculator`](@ref) struct based on the vector of propagators `B` passed to the function.
