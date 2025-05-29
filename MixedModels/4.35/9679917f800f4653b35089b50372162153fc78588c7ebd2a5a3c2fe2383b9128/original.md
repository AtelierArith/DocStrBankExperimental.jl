```
raneftables(m::MixedModel; uscale = false)
```

Return the conditional means of the random effects as a `NamedTuple` of Tables.jl-compliant tables.

!!! note
    The API guarantee is only that the NamedTuple contains Tables.jl tables and not on the particular concrete type of each table.

