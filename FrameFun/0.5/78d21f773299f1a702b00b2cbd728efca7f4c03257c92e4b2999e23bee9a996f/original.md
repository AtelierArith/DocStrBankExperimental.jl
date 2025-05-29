```
abstract type Platform end
```

A platform represents a family of dictionaries.

A platform typically has a primal and a dual sequence. The platform maps an index to a set of parameter values, which is then used to generate a primal or dual dictionary (depending on the chosen measure).

See also [`BasisPlatform`](@ref), `FramePlatform`](@ref)
