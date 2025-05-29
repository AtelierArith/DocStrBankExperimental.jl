```
get_frame(
    daf::DafReader,
    axis::QueryString,
    [columns::Maybe{FrameColumns} = nothing;
    cache::Bool = true]
)::DataFrame end
```

Return a `DataFrame` containing multiple vectors of the same `axis`.

The `axis` can be either just the name of an axis (e.g., `"cell"`), or a query for the axis (e.g., `q"/ cell"`), possibly using a mask (e.g., `q"/ cell & age > 1"`). The result of the query must be a vector of unique axis entry names.

If `columns` is not specified, the data frame will contain all the vector properties of the axis, in alphabetical order (since `DataFrame` has no concept of named rows, the 1st column will contain the name of the axis entry).

By default, this will cache results of all queries. This may consume a large amount of memory. You can disable it by specifying `cache = false`, or release the cached data using [`empty_cache!`](@ref).
