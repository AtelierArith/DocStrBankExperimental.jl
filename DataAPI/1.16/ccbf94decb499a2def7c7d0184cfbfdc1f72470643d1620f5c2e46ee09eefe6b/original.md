```
levels(x; skipmissing=true)
```

Return a vector of unique values which occur or could occur in collection `x`. `missing` values are skipped unless `skipmissing=false` is passed.

Values are returned in the preferred order for the collection, with the result of [`sort`](@ref) as a default. If the collection is not sortable then the order of levels is unspecified.

Contrary to [`unique`](@ref), this function may return values which do not actually occur in the data, and does not preserve their order of appearance in `x`.
