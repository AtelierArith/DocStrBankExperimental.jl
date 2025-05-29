```
supports_in_domain(supports::Union{Real, Vector{<:Real}, Array{<:Real, 2}},
                domain::AbstractInfiniteDomain)::Bool
```

Used to check if `supports` are in the domain of `domain`. Returns `true` if `supports` are in domain of `domain` and returns `false` otherwise. This is primarily an internal method for performing checks but can be extended for user-defined domain types. Extending this is optional, but recommended where possible. Note by fallback, this returns `true` for unrecognized domain types such that an error won't be thrown.
