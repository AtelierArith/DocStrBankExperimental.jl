```
@fieldview fname(x::TYPE) = x.fieldname
@fieldview fname(x::TYPE) = x[i]
...
```

Create a function fieldview that can be accessed by a reversible program

```jldoctest; setup=:(using NiLangCore)
julia> struct GVar{T, GT}
           x::T
           g::GT
       end

julia> @fieldview xx(x::GVar) = x.x

julia> chfield(GVar(1.0, 0.0), xx, 2.0)
GVar{Float64, Float64}(2.0, 0.0)
```
