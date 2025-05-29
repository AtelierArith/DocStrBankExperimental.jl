```
struct SumOfSmallestIntervals <: AbstractRankingCriterion
```

Type for specifying the ranking criterion to be the summed width of all  one-dimensional marginalized smallest intervals containing a probability mass `p`.

Fields:  

  * `p::Float64 = 0.9`: Probability mass to be enclosed in the smallest intervals.
  * `bins::T = 200`: Number of bins for the histograms to calculate interval widths.

Constructors:

```julia
SumOfSmallestIntervals(p=0.9, bins=200)
```
