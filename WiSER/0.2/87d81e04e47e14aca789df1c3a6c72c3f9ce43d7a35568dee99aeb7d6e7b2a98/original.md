```
WSVarLmmModel(meanformula::FormulaTerm, reformula::FormulaTerm, 
wsvarformula::FormulaTerm, idvar::Union{String, Symbol}, tbl)
```

Constructor of `WSVarLmmModel` from a Tables.jl compatible source. 

# Positional arguments

  * `meanformula`: formula for the mean fixed effects β (variables in X matrix).
  * `reformula`: formula for the mean random effects γ (variables in Z matrix).
  * `wsvarformula`: formula for the within-subject variance effects τ (variables in W matrix).
  * `idvar`: id variable for groupings.
  * `tbl:` data table holding all of the data for the model. It can be a

`DataFrame` or column-based table such as an `IndexedTable` from JuliaDB. 

# Keyword arguments

  * `wtvar`: variable name corresponding to the observation weights in the datatable.

# Example

```
vlmm3 = WSVarLmmModel(@formula(y ~ 1 + x2 + x3 + x4 + x5),
    @formula(y ~ 1 + z2 + z3), @formula(y ~ 1 + w2 + w3 + w4 + w5), "id", df)
```
