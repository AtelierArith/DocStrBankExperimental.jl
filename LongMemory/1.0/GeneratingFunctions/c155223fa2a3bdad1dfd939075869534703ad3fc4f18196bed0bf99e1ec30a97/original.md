"     fi*survival*probs(N::Int,d)

Generate the survival probabilities of the error duration model à la Parke (1999).

# Arguments

  * `N::Int`: length of the time series
  * `d::Float64`: fractional difference parameter

# Output

  * `p::Vector`: survival probabilities

# Notes

The survival probabilities are computed using the recursive formula `p_{t+1} = p_t * (t + d - 1) / (t + 1 - d)` to avoid numerical overflow.

# Examples

```julia-repl
julia> fi_survival_probs(100,0.4)
```
