```
parent(@nospecialize(ids::Union{IDS,IDSvector}); IDS_is_absolute_top::Bool=false, error_parent_of_nothing::Bool=true)
```

Return parent IDS/IDSvector in the hierarchy

If `IDS_is_absolute_top=true` then returns `nothing` instead of dd()

If `error_parent_of_nothing=true` then asking `parent(nothing)` will just return nothing
