```
JuMP.set_lower_bound(domain::AbstractInfiniteDomain,
                     lower::Union{Real, Vector{<:Real}})::AbstractInfiniteDomain
```

Set and return the lower bound of `domain` if such an operation makes sense. Errors if the type of `domain` does not support this operation or has not been extended. User-defined domain types should extend this if appropriate.

**Example**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> set_lower_bound(domain, 0.5)
[0.5, 1]
```
