```
stddev(R::TSFrame)
```

Calculates the `standard deviation` of `asset returns`. Output is a `NamedArray`.

# Example

```julia
julia> stddev(returns)
4-element Named Vector{Float64}
σ    │
─────┼──────────
TSLA │  0.149608
NFLX │ 0.0637211
MSFT │ 0.0603753
```
