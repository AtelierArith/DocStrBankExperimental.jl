```
EIndex{C,S} <: SymbolicStateIndex{C,S}
idx = EIndex(comp, sub)
```

A symbolic index for an edge state variable.

  * `comp`: the component index, either int or a collection of ints
  * `sub`: the subindex, either int, symbol or a collection of those.

```
EIndex(1, :P)      # edge 1, variable :P
EIndex(1:5, 1)     # first state of edges 1 to 5
EIndex(7, (:x,:y)) # states :x and :y of edge 7
EIndex(2)          # references the second edge model
```

Can be used to index into objects supporting the `SymbolicIndexingInterface`, e.g. [`NWState`](@ref), [`NWParameter`](@ref) or `ODESolution`.

See also: [`VIndex`](@ref), [`VPIndex`](@ref), [`EPIndex`](@ref)
