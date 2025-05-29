```
SingleComponentFockAddress{N,M} <: AbstractFockAddress{N,M}
```

A type representing a single component Fock state with `N` particles and `M` modes.

Implemented subtypes: [`BoseFS`](@ref), [`FermiFS`](@ref).

# Supported functionality

  * [`find_mode`](@ref)
  * [`find_occupied_mode`](@ref)
  * [`num_occupied_modes`](@ref)
  * [`occupied_modes`](@ref): Lazy iterator.
  * [`OccupiedModeMap`](@ref): `AbstractVector` with eager construction.
  * [`excitation`](@ref): Create a new address.
  * [`BoseFSIndex`](@ref) and [`FermiFSIndex`](@ref) for indexing.

See also [`CompositeFS`](@ref), [`AbstractFockAddress`](@ref).
