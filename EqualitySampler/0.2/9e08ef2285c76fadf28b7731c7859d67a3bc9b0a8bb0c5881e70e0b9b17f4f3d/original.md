```
DirichletProcessPartitionDistribution(k::Integer, α::Float64)
DirichletProcessPartitionDistribution(k::Integer, s::Symbol)
DirichletProcessPartitionDistribution(k::Integer, α::Real)
```

Dirichlet process distribution over partitions. Either set α directly by passing a float, or pass a symbol for a prespecified option. `:Gopalan_Berry` uses `EqualitySampler.dpp_find_α` to specify α, which uses the heuristic by Gopalan & Berry (1998) so that P(everything equal) == P(everything unequal). `harmonic` sets `α` to the inverse of the kth harmonic number, which implies that the prior over partitions is decreasing.
