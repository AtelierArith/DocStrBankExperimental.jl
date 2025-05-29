```
is_point(M::ValidationManifold, p; kwargs...)
```

Perform [`is_point`](@ref) on a [`ValidationManifold`](@ref), where two additional keywords can be used

  * `within=nothing` to specify a function from within which this call was issued
  * `context::NTuple{N,Symbol} where N=()` to specify one or more contexts, this call was issued in. The context `:Point` is added before checking whether the test should be performed

all other keywords are passed on.
