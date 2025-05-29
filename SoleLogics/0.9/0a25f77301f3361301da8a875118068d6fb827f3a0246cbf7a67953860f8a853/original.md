```
const IABase = Union{IntervalRelation,IdentityRel,GlobalRel}
struct RectangleRelation{R1<:IABase,R2<:IABase} <: GeometricalRelation
    x :: R1
    y :: R2
end
```

Relation from 2D interval algebra, obtained from the combination of orthogonal interval relations,  and are thus also referred to as rectangle algebra.

# Examples

```julia-repl
julia> syntaxstring.(IA2DRelations[1:20:end])
9-element Vector{String}:
 "=,A"
 "A,L̅"
 "B,L"
 "E,B̅"
 "O,B"
 "A̅,E̅"
 "B̅,E"
 "E̅,D̅"
 "O̅,D"

julia> length(IA2DRelations)
168
```

See also [`Interval`](@ref), [`Interval2D`](@ref), [`IntervalRelation`](@ref), [`[`GeometricalRelation`](@ref).
