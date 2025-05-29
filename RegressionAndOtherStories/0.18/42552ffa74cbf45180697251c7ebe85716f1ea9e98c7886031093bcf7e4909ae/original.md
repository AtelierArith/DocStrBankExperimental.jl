nested*column*to_array(df, var)

Create a Vector, Matrix or Array from a column of a DataFrame.

```julia
nested_column_to_array(df, var)

```

### Required arguments

```julia
* `df::DataFrame` : DataFrame
* `var::::Union{Symbol, String}` : Column in the DataFrame
```

This is a generalization of the previously available `matrix()` function.

Exported
