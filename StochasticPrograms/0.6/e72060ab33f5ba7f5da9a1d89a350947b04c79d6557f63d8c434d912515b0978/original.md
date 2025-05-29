```
expected(scenarios::Vector{<:AbstractScenario})
```

Return the expected scenario out of the collection `scenarios` in an [`ExpectedScenario`](@ref) wrapper.

This is defined through classical expectation: sum([probability(s)*s for s in scenarios]), and is always defined for scenarios created through @scenario, if the requested fields support it.

Otherwise, user-defined scenario types must implement this method for full functionality.

See also [`ExpectedScenario`](@ref)
