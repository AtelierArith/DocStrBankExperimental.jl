```
minimise(network::AbstractApproximator, x::AbstractMatrix;
    min_decision=nothing, max_decision=nothing,
)
```

Find a minimiser of `network::AbstractApproximator` for given data point `x::AbstractMatrix` using pmap.
