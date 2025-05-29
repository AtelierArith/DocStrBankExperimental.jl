```
infinite_domain(prefs::AbstractArray{<:DependentParameterRef})::InfiniteArrayDomain
```

Return the infinite domain associated with the container of infinite dependent parameters `prefs`. Errors if the container `prefs` is incomplete.

**Example**

```julia-repl
julia> infinite_domain(x)
ZeroMeanDiagNormal(
dim: 2
μ: [0.0, 0.0]
Σ: [1.0 0.0; 0.0 1.0]
)
```
