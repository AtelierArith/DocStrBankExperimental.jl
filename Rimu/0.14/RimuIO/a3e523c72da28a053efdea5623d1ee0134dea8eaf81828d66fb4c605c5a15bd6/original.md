```
RimuIO.save_df(filename, df::DataFrame; kwargs...)
```

Save dataframe in Arrow format.

Keyword arguments are passed on to [`Arrow.write`](https://arrow.apache.org/julia/dev/reference/#Arrow.write). Compression is enabled by default for large `DataFrame`s (over 10,000 rows).

Table-level metadata of the `DataFrame` is saved as Arrow metadata (with `String` value) unless overwritten with the keyword argument `metadata`.

See also [`RimuIO.load_df`](@ref).
