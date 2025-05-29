```
SyncedPolarization{N::Int} <: AbstractIndefinitePolarization
```

An indefinite polarization type, indicating that multiple particles have a synced polarization. Two polarizations are considered synced when they have the same value for `N`. This means that the resulting multiplicity will be 2 total for all particles with the same `SyncedPolarization`.

Having a single `SyncedPolarization{N}` in a process is legal. In this case, it behaves just like an [`AllPolarization`](@ref) would.

See also: [`multiplicity`](@ref)
