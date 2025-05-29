```
C = ccolor(Cdest, Csrc)
```

`ccolor` ("concrete color") supports independent selection of colorspace and numeric element type. `ccolor` chooses the numeric element type from `Cdest` if available, but if not specified gets it from `Csrc`.

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> ccolor(RGB, Gray{Float32})
RGB{Float32}

julia> ccolor(RGB, Gray{N0f8}) == RGB{N0f8}
true

julia> ccolor(RGB{Float32}, Gray{N0f8})
RGB{Float32}
```

Some colorspaces don't support `FixedPoint` numeric element types; in such cases the `eltype_default` for `Cdest` is chosen:

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> ccolor(HSV, RGB{N0f8})
HSV{Float32}
```

`Cdest` can be an abstract type, in which case `Csrc` must be in that abstract color space.

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> ccolor(Color{Float32}, RGB{N0f8})
RGB{Float32}

julia> ccolor(AbstractRGB{Float32}, BGR{N0f8})
BGR{Float32}

julia> ccolor(AbstractRGB{Float32}, HSV{Float32})
ERROR: in ccolor, empty intersection between AbstractRGB and HSV
[...]
```

`ccolor` will throw an error when no unambiguous concrete type can be determined. In the previous case, `AbstractRGB{Float32}` encompases `RGB{Float32}` and `BGR{Float32}`.

`ccolor` is most useful in defining other methods. For example, to allow users to write `convert(RGB, c)` without having to specify the numeric element type of `RGB`, define

```
convert(::Type{C}, p::Colorant) where C<:Colorant = cnvt(ccolor(C,typeof(p)), p)
```

where `cnvt` is the function that performs explicit conversion.
