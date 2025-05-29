```
add_comp!(
    m::Model, comp_id::ComponentId, comp_name::Symbol=comp_id.comp_name;
    first::NothingInt=nothing,
    last::NothingInt=nothing,
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    rename::NothingPairList=nothing
)
```

Add the component indicated by `comp_id` to the model indicated by `m`. The component is added at the end of the list unless one of the keywords `before` or `after` is specified. Note that a copy of `comp_id` is made in the composite and assigned the give name. The optional argument `rename` can be a list of pairs indicating `original_name => imported_name`. The optional  arguments `first` and `last` indicate the times bounding the run period for the given component,  which must be within the bounds of the model and if explicitly set are fixed.  These default  to flexibly changing with the model's `:time` dimension.
