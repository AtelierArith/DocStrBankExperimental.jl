```
chfield(x, field, val)
```

Change a `field` of an object `x`.

The `field` can be a `Val` type

```jldoctest; setup=:(using NiLangCore)
julia> chfield(1+2im, Val(:im), 5)
1 + 5im
```

or a function

```jldoctest; setup=:(using NiLangCore)
julia> using NiLangCore

julia> struct GVar{T, GT}
           x::T
           g::GT
       end

julia> @fieldview xx(x::GVar) = x.x

julia> chfield(GVar(1.0, 0.0), xx, 2.0)
GVar{Float64, Float64}(2.0, 0.0)
```
