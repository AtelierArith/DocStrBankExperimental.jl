```
box() = BOX
box(r::AbstractRelation) = BoxRelationalConnective(r)
```

Return either the box modal connective from unimodal logic (i.e., □), or a a box relational connective from a multi-modal logic, wrapping the relation `r`.

See also [`BoxRelationalConnective`](@ref), [`box`](@ref), [`BOX`](@ref).
