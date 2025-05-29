```
set_infinite_domain(prefs::AbstractArray{<:DependentParameterRef},
                 domain::InfiniteArrayDomain)::Nothing
```

Specify the multi-dimensional infinite domain of the dependent infinite parameters `prefs` to `domain`. Note this will reset/delete all the supports contained in the underlying [`DependentParameters`](@ref) object. This will error if the not all of the dependent infinite parameters are included, if any of them are used by measures.

**Example**

```julia-repl
julia> set_infinite_domain(x, CollectionDomain([IntervalDomain(0, 1), IntervalDomain(0, 2)]))
```
