```
save_results(results, xlfile, paramsets) → (;dfs)
```

Calls the functions [`save_dfs`](@ref), [`save_all_plots`](@ref), [`write_errors`](@ref) to save the results and errors.

# Arguments

  * `results`: `NamedTuple` having structure `(; overview, subsets_results, résumé, errors)`
  * `overview`, `subsets_results`, `résumé`::NamedTuple: Results of actual data processing in the form (; plots=(;df1, df2...), ...).    The key 'plots' is optional.
  * `xlfile`: Path to the XLSX file with the parameter.
  * `paramsets::Vector{NamedTuple}`

# Returned value

  * `(;dfs)`: A NamedTuple of DataFrames as returned by [`save_dfs`](@ref)

Function `save_results` is public, not exported.
