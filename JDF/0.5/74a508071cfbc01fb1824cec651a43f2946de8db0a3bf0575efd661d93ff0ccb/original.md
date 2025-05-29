```
type_compress!(df, compress_float = false, verbose = false)
```

Compress a DataFrame by using types of smaller bit. If safe to do so, it will "downgrade" `Int*` and `UInt*` if safe to do some. It will compress any `CategoricalVector` with `DataFrames.compress`.

For `Vector{String}`, if the number unique values is less than 2^16 then it will be converted to `CategoricalVector` and otherwise will be stored as `WeakRefStrings.StringVector`.

If `compress_float = true` then `Float64` will be downgraded to `Float32`; but beware that this means the calculation will be done with reduce precision.
