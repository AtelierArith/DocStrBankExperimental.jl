```
ModelMap(Map::Function, InDomain::Union{Nothing,Function}, Domain::HyperCube; startp::AbstractVector)
ModelMap(Map::Function, InDomain::Function, xyp::Tuple{Int,Int,Int})
```

A container which stores additional information about a model map, in particular its domain of validity. `Map` is the actual map `(x,θ) -> model(x,θ)`. `Domain` is a `HyperCube` which allows one to roughly specify the ranges of the various parameters. For more complicated boundary constraints, a function `InDomain(θ)` can be specified, for which all outputted components should be .≥ 0 on the valid parameter domain. Alternatively, `InDomain` may also be a bool-valued function, evaluating to `true` in admissible parts of the parameter domain.

The kwarg `startp` may be used to pass a suitable parameter vector for the ModelMap.
