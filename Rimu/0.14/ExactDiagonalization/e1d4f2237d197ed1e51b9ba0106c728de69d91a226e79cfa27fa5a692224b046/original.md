```
build_basis(addr::AbstractFockAddress)
build_basis(::Type{<:AbstractFockAddress}) -> basis
```

Return all possible Fock states of a given type as a vector. This method is *much* faster than `build_basis(::AbstractHamiltonian, ...)`, but does not take matrix blocking into account. This version of `build_basis` accepts no additional arguments.

All address types except [`OccupationNumberFS`](@ref Main.Rimu.OccupationNumberFS) are supported.

Returns a sorted vector of length equal to the [`dimension`](@ref) of `addr`.

See also [`AbstractFockAddress`](@ref).
