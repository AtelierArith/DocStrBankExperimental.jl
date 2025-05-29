```
OneHotEncoder(Dict(
   # Nominal columns
   :nominal_columns => Int[],

   # Nominal column values map. Key is column index, value is list of
   # possible values for that column.
   :nominal_column_values_map => Dict{Int,Any}()
))
```

Transforms myinstances with nominal features into one-hot form and coerces the instance matrix to be of element type Float64.

Implements `fit!` and `transform`.
