```
sum(A::Vector{MPS}; kwargs...)

sum(A::Vector{MPO}; kwargs...)
```

Add multiple MPS/MPO with each other, with some optional truncation.

# Keywords

  * `cutoff::Real`: singular value truncation cutoff
  * `maxdim::Int`: maximum MPS/MPO bond dimension
