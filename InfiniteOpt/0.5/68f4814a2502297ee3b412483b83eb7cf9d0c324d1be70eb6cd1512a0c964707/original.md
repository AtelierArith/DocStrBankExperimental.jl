```
JuMP.upper_bound(domain::AbstractInfiniteDomain)::Union{Real, Vector{<:Real}}
```

Return the upper bound of `domain` if one exists. This should be extended for user-defined infinite domains if appropriate. Errors if `JuMP.has_upper_bound` returns `false`. Extensions are enabled by `JuMP.has_upper_bound(domain)` and `JuMP.upper_bound(domain)`.

**Example**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> upper_bound(domain)
1.0
```
