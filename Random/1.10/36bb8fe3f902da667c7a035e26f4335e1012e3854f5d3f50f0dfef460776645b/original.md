```
randn!([rng=default_rng()], A::AbstractArray) -> A
```

Fill the array `A` with normally-distributed (mean 0, standard deviation 1) random numbers. Also see the [`rand`](@ref) function.

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> randn!(rng, zeros(5))
5-element Vector{Float64}:
  0.8673472019512456
 -0.9017438158568171
 -0.4944787535042339
 -0.9029142938652416
  0.8644013132535154
```
