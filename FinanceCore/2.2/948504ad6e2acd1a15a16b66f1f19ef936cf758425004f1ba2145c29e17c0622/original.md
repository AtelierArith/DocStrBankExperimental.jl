```
internal_rate_of_return(cashflows::vector)::Rate
internal_rate_of_return(cashflows::Vector, timepoints::Vector)::Rate
```

Calculate the internal*rate*of_return with given timepoints. If no timepoints given, will assume that a series of equally spaced cashflows, assuming the first cashflow occurring at time zero and subsequent elements at time 1, 2, 3, ..., n. 

Returns a Rate type with periodic compounding once per period (e.g. annual effective if the `timepoints` given represent years). Get the scalar rate by calling `Yields.rate()` on the result.

# Example

```julia-repl
julia> internal_rate_of_return([-100,110],[0,1]) # e.g. cashflows at time 0 and 1
0.10000000001652906
julia> internal_rate_of_return([-100,110]) # implied the same as above
0.10000000001652906
```

# Solver notes

Will try to return a root within the range [-2,2]. If the fast solver does not find one matching this condition, then a more robust search will be performed over the [.99,2] range.

The solution returned will be in the range [-2,2], but may not be the one nearest zero. For a slightly slower, but more robust version, call `ActuaryUtilities.irr_robust(cashflows,timepoints)` directly.
