```
missing_outcomes(o::OutcomeSpace, x; all = false) → n::Int
```

Count the number of missing outcomes `n` (i.e., not occuring in the data) specified by `o`, given input data `x`. This function only works for count-based outcome spaces, use [`missing_probabilities`](@ref) otherwise.

See also: [`MissingDispersionPatterns`](@ref).
