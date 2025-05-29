```
EGE{T<:AbstractFloat}<:EGMFramework
```

EGE variant of the EGM algorithm.

# Fields

  * `gamma1::T`: momentum parameter

# Example

```julia
julia> model = EGE(0.99)
EGE{Float64}(0.99)
```
