```
function nnodes(f::DecisionForest)
```

Return the number of nodes within `f`, that is, the sum of the nodes number in each wrapped [`DecisionTree`](@ref).

See also [`DecisionForest`](@ref), [`DecisionTree`](@ref).
