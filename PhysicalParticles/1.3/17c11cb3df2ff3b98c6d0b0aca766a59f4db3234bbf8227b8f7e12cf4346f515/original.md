```
struct PVector2D{T<:Number} <: AbstractPoint2D{T}
```

## Fields

  * x::T
  * y::T

## Examples

```jl
julia> PVector2D()
PVector2D{Float64}(0.0, 0.0)

julia> PVector2D(u"m")
PVector2D(0.0 m, 0.0 m)

julia> PVector(1.0im, 2.0 + 3.0im)
PVector2D{ComplexF64}(0.0 + 1.0im, 2.0 + 3.0im)
```
