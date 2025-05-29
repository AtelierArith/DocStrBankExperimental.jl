```
JuMP.lower_bound(domain::AbstractInfiniteDomain)::Union{Real, Vector{<:Real}}
```

Return the lower bound of `domain` if one exists. This should be extended for user-defined infinite domains if appropriate. Errors if `JuMP.has_lower_bound` returns `false`. Extensions are enabled by `JuMP.has_lower_bound(domain)` and `JuMP.lower_bound(domain)`.

**Example**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> lower_bound(domain)
0.0
```
