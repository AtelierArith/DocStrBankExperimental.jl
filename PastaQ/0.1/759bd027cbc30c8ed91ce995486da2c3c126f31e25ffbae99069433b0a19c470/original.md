```
randomlayer(
  gatenames::Vector{<:AbstractString},
  support::Union{Vector{<:Int}, AbstractRange, Vector{<:Tuple}};
  rng=Random.GLOBAL_RNG,
  weights::Union{Nothing,Vector{Float64}} = ones(length(gatenames)) / length(gatenames),
  kwargs...,
)
```

Generate a random layer built out of one or two qubit gates, where `gatenames` is a set of possible gates to choose from. By default, each single gate is sampled uniformaly over this set. If `weights` are provided, each gate is sampled accordingly.

```julia
randomlayer(["X","Y","Z"], 3)
# 3-element Vector{Any}:
#  ("Y", 1)
#  ("Y", 2)
#  ("X", 3)
```
