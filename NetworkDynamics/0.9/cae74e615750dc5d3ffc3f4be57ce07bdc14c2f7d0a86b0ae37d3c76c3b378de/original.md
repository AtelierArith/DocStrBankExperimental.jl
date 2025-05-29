```
VPIndex{C,S} <: SymbolicStateIndex{C,S}
idx = VPIndex(comp, sub)
```

A symbolic index into the parameter a vertex:

  * `comp`: the component index, either int or a collection of ints
  * `sub`: the subindex, either int, symbol or a collection of those.

Can be used to index into objects supporting the `SymbolicIndexingInterface`, e.g. [`NWParameter`](@ref) or `ODEProblem`.

See also: [`EPIndex`](@ref), [`VIndex`](@ref), [`EIndex`](@ref)
