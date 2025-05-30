```
summarize(chains, funs...[; sections, func_names = [], name = "", append_chains = true])
```

Summarize `chains` in a `ChainsDataFrame`.

# Examples

  * `summarize(chns)` : Complete chain summary
  * `summarize(chns[[:parm1, :parm2]])` : Chain summary of selected parameters
  * `summarize(chns; sections=[:parameters])`  : Chain summary of :parameters section
  * `summarize(chns; sections=[:parameters, :internals])` : Chain summary for multiple sections
