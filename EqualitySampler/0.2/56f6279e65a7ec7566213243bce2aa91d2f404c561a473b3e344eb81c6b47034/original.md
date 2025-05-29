```julia
unsignedstirlings1(n::Integer, k::Integer) -> Any

```

Compute the absolute value of the Stirlings numbers of the first kind. The `EqualitySampler.ExplicitStrategy` (default) uses an explicit loop and is computationally more efficient but subject to overflow, so using BigInt is advised. The `EqualitySampler.RecursiveStrategy` uses recursion and is mathematically elegant yet inefficient for large values.
