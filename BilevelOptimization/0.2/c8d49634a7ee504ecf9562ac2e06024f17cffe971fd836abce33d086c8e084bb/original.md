```
`build_blp_model(m, B, d, x, y, s, F; [comp_method])`
```

Build the bilevel JuMP model from the data without grouping everything into a `BilevelLP`. An optional keyword `comp_method` can be passed for handling complementarity constraints, default is `SOS1Complementarity`.
