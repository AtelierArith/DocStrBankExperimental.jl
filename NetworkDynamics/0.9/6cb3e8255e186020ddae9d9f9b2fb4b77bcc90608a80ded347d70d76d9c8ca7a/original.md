```
VIndex{C,S} <: SymbolicStateIndex{C,S}
idx = VIndex(comp, sub)
```

A symbolic index for a vertex state variable.

  * `comp`: the component index, either int or a collection of ints
  * `sub`: the subindex, either int, symbol or a collection of those.

```
VIndex(1, :P)      # vertex 1, variable :P
VIndex(1:5, 1)     # first state of vertices 1 to 5
VIndex(7, (:x,:y)) # states :x and :y of vertex 7
VIndex(2)          # references the second vertex model
```

Can be used to index into objects supporting the `SymbolicIndexingInterface`, e.g. [`NWState`](@ref), [`NWParameter`](@ref) or `ODESolution`.

See also: [`EIndex`](@ref), [`VPIndex`](@ref), [`EPIndex`](@ref)
