```
Cbase = base_colorant_type(C::Type)
Cbase = base_colorant_type(c::Colorant)
```

Return the Colorant type without specified numeric element type.

For example, compare

```
base_colorant_type(ARGB{N0f8}) === ARGB
```

vs

```
base_color_type(ARGB{N0f8})    === RGB
color_type(ARGB{N0f8})         === RGB{N0f8}
```

When possible, `base_colorant_type` returns a parametric `UnionAll`, so that `Cbase{T}` can be used to specify a colorant with element type `T`. However, `base_colorant_type` is not guaranteed to return a parametric result, for example

```jldoctest; setup = :(using ColorTypes)
julia> base_colorant_type(RGB24)
RGB24
```

In generic code, you can check whether `Cbase` is a `DataType` or `UnionAll`; `Cbase{T}` will be valid only if it's a `UnionAll`.

# Usage example

A safe and easy way to switch the element type of a colorant value `c` to be `Float64` is

```
Cbase = base_colorant_type(parametric_colorant(typeof(c)))
c64 = Cbase{Float64}(c)
```
