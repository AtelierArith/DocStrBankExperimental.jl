```
EGA{T<:AbstractFloat}<:EGMFramework
```

EGA variant of the EGM algorithm.

# Fields

  * `gamma1::T`: momentum parameter
  * `gamma2::T`: momentum parameter

# Example

```julia
julia> model = EGA(0.99, 0.)
EGA{Float64}(0.99, 0.0)
```
