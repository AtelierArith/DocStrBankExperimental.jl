```
getdataframe(m::AbstractModel, comp_name::Symbol, pairs::Pair{Symbol, Symbol}...)
```

Return a DataFrame with values for the given variables or parameters of model `m` indicated by `pairs`, where each pair is of the form `comp_name => item_name`. If more than one pair is provided, all must refer to items with the same dimensions, which are used to join the respective item values.
