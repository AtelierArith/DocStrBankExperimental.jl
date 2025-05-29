```
first_treated_period_ids(x <: BalancedPanel)

Returns the indices of the first treated period for each treated units, that is, a Vector{Int}
of length Nₜᵣ, where each element is the index of the first 1 in the row of treatment matrix W
corresonding to the treatment unit. 

For a single treated unit, returns only the index of the first treated period. For multiple
```
