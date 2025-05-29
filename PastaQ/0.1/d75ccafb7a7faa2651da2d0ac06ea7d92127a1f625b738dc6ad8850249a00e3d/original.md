```
randomlayer(
  gatename::AbstractString,
  support::Union{Int, Vector{<:Tuple}, AbstractRange};
  rng = Random.GLOBAL_RNG,
  kwargs...
)
```

Generate a random layer built out of a set one or two qubit gates If `support::Int = n`, generates $n$ single-qubit gates `gatename`. If `support::Vector=bonds`, generates a set of two-qubit gates on the couplings contained in `support`.

```julia
randomlayer("Ry", 3)
# 3-element Vector{Any}:
#  ("Ry", 1, (θ = 0.5029516521736083,))
#  ("Ry", 2, (θ = 2.5324545964433693,))
#  ("Ry", 3, (θ = 2.0510824561219523,))
```
