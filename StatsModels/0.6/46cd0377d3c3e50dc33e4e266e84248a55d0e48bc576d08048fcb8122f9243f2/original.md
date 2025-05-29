```
ContinuousTerm <: AbstractTerm
```

Represents a continuous variable, with a name and summary statistics.

# Fields

  * `sym::Symbol`: The name of the variable
  * `mean::T`: Mean
  * `var::T`: Variance
  * `min::T`: Minimum value
  * `max::T`: Maximum value
