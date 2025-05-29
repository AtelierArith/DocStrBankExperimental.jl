```
show_links(vardom::VariableDomain)
show_links(model::Model, varnamefull::AbstractString)
show_links(io::IO, vardom::VariableDomain)
show_links(io::IO, model::Model, varnamefull::AbstractString)
```

Display all [`VariableReaction`](@ref)s linked to this [`VariableDomain`](@ref)

`varnamefull` should be of form "<domain name>.<variable name>"

Linked variables are shown as "<domain name>.<reaction name>.<method name>.<local name>"
