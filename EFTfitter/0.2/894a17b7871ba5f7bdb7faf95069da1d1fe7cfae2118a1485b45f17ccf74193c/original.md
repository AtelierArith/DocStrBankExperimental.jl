```
struct SmallestInterval <: AbstractRankingCriterion
```

Type for specifying the ranking criterion to be the total width of the one-dimensional marginalized smallest interval containing a probability mass `p` for a certain parameter.

Fields:  

  * `key::Symbol`: Name of the parameter that is used for the marginalized intervals.
  * `p::Float64 = 0.9`: Probability mass to be enclosed in the smallest interval.

Constructors:

```julia
SmallestInterval(key::Symbol, p=0.9, bins=200)
```
