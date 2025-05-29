```
set_infinite_domain(pref::DependentParameterRef,
                 domain::InfiniteScalarDomain)::Nothing
```

Specify the scalar infinite domain of the dependent infinite parameter `pref` to `domain` if `pref` is part of a [`CollectionDomain`](@ref), otherwise an error is thrown. Note this will reset/delete all the supports contained in the underlying [`DependentParameters`](@ref) object. Also, errors if `pref` is used by a measure.

**Example**

```julia-repl
julia> set_infinite_domain(x[1], IntervalDomain(0, 2))

julia> infinite_domain(x[1])
[0, 2]
```
