```
const IABase = Union{IntervalRelation,IdentityRel,GlobalRel}
struct RectangleRelation{R1<:IABase,R2<:IABase} <: GeometricalRelation
    x :: R1
    y :: R2
end
```

2D区間代数からの関係で、直交区間関係の組み合わせから得られ、したがって長方形代数とも呼ばれます。

# 例

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

関連項目としては [`Interval`](@ref), [`Interval2D`](@ref), [`IntervalRelation`](@ref), [`GeometricalRelation`](@ref) があります。
