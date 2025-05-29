```
get_diffs(mg::MetaGraphsNext.MetaGraph)
```

Uses the JuMP Models stored in mg.graph_data[:models] to calculate the difference between power injections/loads, and |v| at every leaf/substation connection. 

returns three `Float64[]`
