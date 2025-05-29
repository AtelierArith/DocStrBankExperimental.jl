```
JuMP.set_upper_bound(domain::AbstractInfiniteDomain,
                     upper::Real)::AbstractInfiniteDomain
```

Set and return the upper bound of `domain` if such an aoperation makes sense. Errors if the type of `domain` does not support this operation or has not been extended. User-defined domain types should extend this if appropriate.

**Example**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> set_upper_bound(domain, 0.5)
[0, 0.5]
```
