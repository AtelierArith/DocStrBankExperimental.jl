```
infinite_domain(pref::DependentParameterRef)::InfiniteScalarDomain
```

Return the infinite domain associated with the particular infinite dependent parameter `pref` if valid. Errors if the underlying [`DependentParameters`](@ref) object does not use a [`CollectionDomain`](@ref).

**Example**

```julia-repl
julia> infinite_domain(x[1])
[-1, 1]
```
