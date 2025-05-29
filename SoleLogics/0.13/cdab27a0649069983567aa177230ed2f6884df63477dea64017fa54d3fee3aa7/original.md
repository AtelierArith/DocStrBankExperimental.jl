```
struct FilteredRelation{R<:AbstractRelation,F<:WorldFilter} <: AbstractRelation
    r::R
    wf::F
end
```

A (binary) accessibility relation `r`, filtered by a world filter `wf`.
