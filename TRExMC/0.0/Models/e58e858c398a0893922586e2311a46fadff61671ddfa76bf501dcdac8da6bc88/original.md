```
Model{L, H[, O]}
```

The main container used for simulations. The type parameters are given by

  * `L <:`[`AbstractLattice`](@ref)
  * `H <:`[`AbstractHamiltonian`](@ref)
  * `O <:`[`AbstractObservable`](@ref)

      * If no observable is provided, then the [`NullObservable`](@ref) is used.
