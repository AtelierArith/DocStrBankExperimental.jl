```
replace_comp!(
    m::Model, comp_def::ComponentDef, comp_name::Symbol=comp_id.comp_name;
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    reconnect::Bool=true
)
```

Deprecated function for replacing the component with name `comp_name` in model `m` with the  new component specified by `comp_def`. Use the following syntax instead:

`replace!(m, comp_name => comp_def; kwargs...)`

See docstring for `replace!` for further description of available functionality.
