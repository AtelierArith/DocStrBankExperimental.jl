```
nodid = addnode!(model,coord)
```

If `coord` is an `AbstractVector` of `Real`: add a single node to the model.   Muscade does not prescribe what coordinate system to use.  Muscade will handle  to each element the `coord` of the nodes of the element, and the element  constructor must be able to make sense of it. `nodid` is a node identifier, that is used as input to `addelement!`.

If `coord` is an `AbstractMatrix`, its rows are treated as vectors of coordinates. `nodid` is then a vector of node identifiers.

See also: [`addelement!`](@ref), [`coord`](@ref) , [`describe`](@ref) 
