```julia
stan_variables(dct, df)

```

Given a dictionary of `Variable` objects and a source  DataFrame, extract the variables from the source array and reshape them to the correct dimensions.

## Parameters

parameters::OrderedDict{String, Variable}

```
A dictionary of `Variable` objects, 
like that returned by `parse_header()`.
```

df::DataFrame

```
A DataFrame (as returned from `read_csvfiles()`
or `read_samples(model, :dataframe)`) to 
extract the draws from.
```

## Returns

```
A, possibly nested, DataFrame with reshaped fields.
```

Exported.
