```
update!(o::Optimizer{<:BFGSOptimizer}, C, B)
```

Peform an update with the BFGS optimizer. 

`C` is the cache, `B` contains the gradient information (the output of [`global_rep`](@ref) in general).

First we compute the *final velocity* with

```julia
vecS = -o.method.η * C.H * vec(B)
```

and then we update `H`

```julia
C.H .= (𝕀 - ρ * SY) * C.H * (𝕀 - ρ * SY') + ρ * vecS * vecS'
```

where `SY` is `vecS * Y'` and `𝕀` is the idendity. 

# Implementation

For stability we use `δ` for computing `ρ`:

```julia
ρ = 1. / (vecS' * Y + o.method.δ)
```

This is similar to the [`AdamOptimizer`](@ref)

# Extended help

If we have weights on a [`Manifold`](@ref) than the updates are slightly more difficult. In this case the [`vec`](@ref) operation has to be generalized to the corresponding *global tangent space*.
