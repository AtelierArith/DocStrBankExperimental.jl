```
MonoLightField2D  <: AbstractLightField2D
```

`MonoLightField2D` is used to represent a 2-dimensional monochromatic light field.

# Examples

```jldoctest; setup = :(using OpticalPropagation)
julia> using Unitful

julia> MonoLightField2D([1 2; 3 4],wavelength=632.8u"nm",size=(1u"mm",1u"mm"))
MonoLightField2D:
    wavelength: 6.328e-7 m
    physical size: (0.001 m, 0.001 m)
    complex amplitude data:
2×2 Array{Complex{Float64},2}:
 1.0+0.0im  2.0+0.0im
 3.0+0.0im  4.0+0.0im
```
