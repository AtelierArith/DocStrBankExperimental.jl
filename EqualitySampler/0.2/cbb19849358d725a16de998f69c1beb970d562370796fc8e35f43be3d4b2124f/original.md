```
stirlings2r(n::T, k::T, r::T) where T <: Integer
stirlings2r(n::T, k::T, r::T, ::Type{EqualitySampler.ExplicitStrategy})  where T <: Integer
stirlings2r(n::T, k::T, r::T, ::Type{EqualitySampler.RecursiveStrategy}) where T <: Integer
```

Compute the r-Stirlings numbers of the second kind. The `EqualitySampler.ExplicitStrategy` (default) uses an explicit loop and is computationally more efficient but subject to overflow, so using BigInt is advised. The `EqualitySampler.RecursiveStrategy` uses recursion and is mathematically elegant yet inefficient for large values.
