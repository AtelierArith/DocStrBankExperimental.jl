```
show_parameters(model) -> DataFrame
```

Get parameters for all reactions in model.

# Examples:

Show all model parameters using VS Code table viewer:

```
julia> vscodedisplay(PB.show_parameters(run.model))
```

Write out all model parameters as csv for import to a spreadsheet:

```
julia> CSV.write("pars.csv", PB.show_parameters(run.model))
```
