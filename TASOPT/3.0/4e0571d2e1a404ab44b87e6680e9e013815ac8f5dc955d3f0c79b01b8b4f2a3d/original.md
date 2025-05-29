```
generate_par_indname(par_suffix::AbstractVector{String}=["i","g","m","a","e"])
```

Given a vector of String suffixes, calls `generate_par_indname(par_suffix::String)` for each  and saves to a `Dict` with key `"par"*par_suffix` and returns the `Dict`.  Defaults to the par_arrays of the default model.
