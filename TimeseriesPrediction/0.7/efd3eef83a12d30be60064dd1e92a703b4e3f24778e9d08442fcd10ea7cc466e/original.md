```
SpatioTemporalEmbedding{Φ,BC,X} → embedding
```

A spatio temporal delay coordinates structure to be used as a functor. Applies to data of `Φ` spatial dimensions and gives an embedding of dimensionality `X`.

```
embedding(rvec, s, t, α)
```

Operates inplace on `rvec` (of length `X`) and reconstructs vector from spatial timeseries `s` at timestep `t` and cartesian index `α`. Note that there are no bounds checks for `t`.

It is assumed that `s` is a `Vector{<:AbstractArray{T,Φ}}`.

## Constructors

There are some convenience constructors that return intuitive embeddings here:

  * [`cubic_shell_embedding`](@ref)
  * [`light_cone_embedding`](@ref)

The "main" constructor is

```
SpatioTemporalEmbedding{X}(τ, β, bc, fsize)
```

which allows full control over the spatio-temporal embedding.

  * `Χ == length(τ) == length(β)` : dimensionality of resulting reconstructed space.
  * `τ::Vector{Int}` = Vector of temporal delays **for each entry** of the reconstructed space (sorted in ascending order).
  * `β::Vector{CartesianIndex{Φ}}` = vector of *relative* indices of spatial delays *for each entry* of the reconstructed space.
  * `bc::BC` : boundary condition.
  * `fsize::NTuple{Φ, Int}` : Size of each state in the timeseries.

For example, if you want to have spatial neighbors [0, ±1] for time delays τ = 2, 4, then

```
τ = [2,2,2,4,4,4]
β = CartesianIndex.([1, 0, -1, 1, 0, -1])
```
