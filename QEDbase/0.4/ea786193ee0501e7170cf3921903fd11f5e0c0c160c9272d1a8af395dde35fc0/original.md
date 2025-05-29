```
SyncedSpin{N::Int} <: AbstractIndefiniteSpin
```

An indefinite spin type, indicating that multiple particles have a synced spin. Two spins are considered synced when they have the same value for `N`. This means that the resulting multiplicity will be 2 total for all particles with the same `SyncedSpin`.

Having a single `SyncedSpin{N}` in a process is legal. In this case, it behaves just like an [`AllSpin`](@ref) would.

See also: [`multiplicity`](@ref)
