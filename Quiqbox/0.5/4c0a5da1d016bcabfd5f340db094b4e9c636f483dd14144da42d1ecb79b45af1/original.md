```
hasApprox(obj1, obj2, obj3...; ignoreFunction::Bool=false, ignoreContainer::Bool=false,
          decomposeNumberCollection::Bool=false, atol::Real=1e-15) -> 
Bool
```

Similar to [`hasEqual`](@ref), except it does not require the `Number`-typed fields  (e.g. `Float64`) of the compared containers to have the exact same values, but rather the  approximate values within an error threshold determined by `atol`, like in `isapprox`.
