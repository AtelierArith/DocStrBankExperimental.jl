```
is_conditional_distribution( probabilities :: AbstractMatrix{<:Real}; atol=ATOL :: Flaot64 ) :: Bool
```

Returns `true` if the provided matrix is column stochastic. That is, each column is a valid probability distribution.
