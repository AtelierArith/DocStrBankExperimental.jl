```
replace_comp!(
    m::Model, comp_id::ComponentId, comp_name::Symbol=comp_id.comp_name;
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    reconnect::Bool=true
)
```

Deprecated function for replacing the component with name `comp_name` in model `m` with the  new component specified by `comp_id`. Use the following syntax instead:

`replace!(m, comp_name => Mimi.compdef(comp_id); kwargs...)`

See docstring for `replace!` for further description of available functionality.
