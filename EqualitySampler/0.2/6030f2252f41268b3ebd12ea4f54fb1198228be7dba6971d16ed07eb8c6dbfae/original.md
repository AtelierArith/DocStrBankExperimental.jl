```julia
stirlings2(n::Integer, k::Integer) -> Any
stirlings2(
    n::Integer,
    k::Integer,
    S::Type{<:EqualitySampler.StirlingStrategy}
) -> Any

```

Compute the Stirlings numbers of the second kind. The `EqualitySampler.ExplicitStrategy` (default) uses an explicit loop and is computationally more efficient but subject to overflow, so using BigInt is advised. The `EqualitySampler.RecursiveStrategy` uses recursion and is mathematically elegant yet inefficient for large values.
