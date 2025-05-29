```
indVarOf(pb::ParamBox{T}) -> Pair{}
```

Return (the name and the value of) the independent variable tied to `pb`. Specifically,  return the input variable stored in `pb` when `pb` is marked as differentiable; return the  output variable of `pb` when `pb` is marked as non-differentiable. Thus, it is the variable  `pb` represents to differentiate any (differentiable) function of [`ParamBox`](@ref)es.
