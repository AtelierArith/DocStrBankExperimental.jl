```
JuMP.has_lower_bound(domain::AbstractInfiniteDomain)::Bool
```

Return `Bool` indicating if `domain` has a lower bound that can be determined. This should be extended for user-defined infinite domains. It defaults to `false` for unrecognized domain types.

**Example**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> has_lower_bound(domain)
true
```
