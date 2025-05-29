```
struct FilteredRelation{R<:AbstractRelation,F<:WorldFilter} <: AbstractRelation
    r::R
    wf::F
end
```

バイナリのアクセシビリティ関係 `r` は、ワールドフィルター `wf` によってフィルタリングされます。
