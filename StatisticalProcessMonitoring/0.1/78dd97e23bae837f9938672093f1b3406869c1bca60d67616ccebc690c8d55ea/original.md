```
Phase2Distribution{T} <: AbstractPhase2
```

A struct that is used to generate and new data from a distribution. It contains a sampleable field `dist` of type `T`, which represents the underlying data-generating process.

### Notes

A method `rand(::T)` is required to generate new data from `dist`.

### Example

```
using Distributions
DGP = Phase2Distribution(Normal(0,1))
new_data(DGP)
```
