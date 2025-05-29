```julia
convert_categorical_columns!(df)

```

Removes columns of `df` which are stored as `PooledArray` (assumed to encode categorical features), and replace them with as many new binary columns as needed to encode all the possible categorical features. New columns are added at the end of the `df`.
