```
rels(M::AbstractAlgebra.FPModule{T}) where T <: RingElement
```

Return a vector of all the relations between generators of the given module, where each relation is given as row matrix. The relation matrix whose rows are the returned relations will be in reduced form (hnf/rref).
