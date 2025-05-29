```
Constrained
```

Instance of a [`ConditionType`](@ref) used for declaring that an edge has a `Constrained` condition. When an edge has this condition associated with it,  it will be treated as any normal edge and no boundary condition will be applied. With this condition, it is assumed that you will later setup your problem as a  differential-algebraic equation (DAE) and provide the appropriate constraints. See the docs for some examples.

When you provide a `Constrained` condition, for certain technical reasons  you do still need to provide a function that corresponds to it in the function list  provided to [`BoundaryConditions`](@ref). For this function, any function will work,  e.g. `sin` - it will not be called. The proper constraint function is to be provided after-the-fact,  as explained in the docs.
