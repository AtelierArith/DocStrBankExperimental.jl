```
NamedTupleDist <: MultivariateDistribution
NamedTupleDist <: MultivariateDistribution
```

A distribution with `NamedTuple`-typed variates.

`NamedTupleDist` provides an effective mechanism to specify the distribution of each variable/parameter in a set of named variables/parameters.

Calling `varshape` on a `NamedTupleDist` will yield a [`NamedTupleShape`](@ref).
