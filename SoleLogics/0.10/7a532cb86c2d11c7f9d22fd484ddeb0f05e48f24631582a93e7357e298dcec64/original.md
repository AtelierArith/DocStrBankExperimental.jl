```
diamond() = DIAMOND
diamond(r::AbstractRelation) = DiamondRelationalConnective(r)
```

Return either the diamond modal connective from unimodal logic (i.e., ◊), or a a diamond relational connective from a multi-modal logic, wrapping the relation `r`.

See also [`DiamondRelationalConnective`](@ref), [`diamond`](@ref), [`DIAMOND`](@ref).
