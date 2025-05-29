```
show_variables(model::Model; [attributes], [filter], showlinks=false, modeldata=nothing) -> DataFrame
show_variables(model::Model, domainname; [attributes], [filter], showlinks=false, modeldata=nothing) -> DataFrame
```

Show table of Domain Variables. Optionally get variable links, data.

# Keywords:

See [`show_variables(domain::Domain, kwargs...)`](@ref) 

# Examples:

Display all model Variables using VS Code table viewer:

```
julia> vscodedisplay(PB.show_variables(run.model))
```

Write out all model Variables as csv for import to a spreadsheet:

```
julia> CSV.write("vars.csv", PB.show_variables(run.model, modeldata=modeldata, showlinks=true))
```
