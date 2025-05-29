```
struct PVector{T<:Number} <: AbstractPoint3D{T}
```

## Fields

  * x::T
  * y::T
  * z::T

## Examples

```jl
julia> PVector()
PVector{Float64}(0.0, 0.0, 0.0)

julia> PVector(u"m")
PVector(0.0 m, 0.0 m, 0.0 m)

julia> PVector() * im
PVector{ComplexF64}(0.0 + 0.0im, 0.0 + 0.0im, 0.0 + 0.0im)
```
