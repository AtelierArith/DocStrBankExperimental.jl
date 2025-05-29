```
struct HighestDensityRegion <: AbstractRankingCriterion
```

Type for specifying the ranking criterion to be the area of the two-dimensional  marginal posterior region containing a probability mass `p` for two certain parameters.

Fields:  

  * `keys::NTuple{2, Symbol}`: Names of the parameters that are used for the marginalized regions.
  * `p::Float64 = 0.9`: Probability mass to be enclosed in the smallest interval.
  * `bins::T = 200`: Number of bins for the histograms to calculate interval widths.

Constructors:

```julia
HighestDensityRegion(keys::NTuple{2, Symbol}, p=0.9, bins=200)
```
