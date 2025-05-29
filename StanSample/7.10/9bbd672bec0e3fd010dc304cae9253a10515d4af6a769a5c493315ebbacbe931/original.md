Create a StanSummary

```julia
describe(model, params; round_estimates, digits)

```

## Required positional arguments

```julia
* `model::SampleModel` # SampleModel used to create the draws
```

## Optional positional arguments

```julia
* `params` # Vector of Symbols or Strings to be included
```

## Keyword arguments

```julia
* `round_estimates = true` #
* `digits = 3` # Number of decimal digits
```

## Returns

A StanSummary object.
