```
describe_example_data(name) -> String
```

Return a string containing descriptions of all available datasets.

# Examples

```jldoctest
julia> describe_example_data("radon") |> println
radon
=====

Radon is a radioactive gas that enters homes through contact points with the ground. It is a carcinogen that is the primary cause of lung cancer in non-smokers. Radon levels vary greatly from household to household.

This example uses an EPA study of radon levels in houses in Minnesota to construct a model with a hierarchy over households within a county. The model includes estimates (gamma) for contextual effects of the uranium per household.

See Gelman and Hill (2006) for details on the example, or https://docs.pymc.io/notebooks/multilevel_modeling.html by Chris Fonnesbeck for details on this implementation.

remote: http://ndownloader.figshare.com/files/24067472
```
