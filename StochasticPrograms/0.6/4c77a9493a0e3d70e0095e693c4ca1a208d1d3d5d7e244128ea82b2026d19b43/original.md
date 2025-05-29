```
probability(scenario::AbstractScenario)
```

Return the probability of `scenario` occuring.

Is always defined for scenarios created through @scenario. Other user defined scenario types must implement this method to generate a proper probability. The default behaviour is to assume that `scenario` has a `probability` field of type [`Probability`](@ref)

See also: [`Probability`](@ref)
