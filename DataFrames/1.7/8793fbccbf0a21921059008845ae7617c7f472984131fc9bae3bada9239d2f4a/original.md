```
copy(dfr::DataFrameRow)
```

Construct a `NamedTuple` with the same contents as the [`DataFrameRow`](@ref). This method returns a `NamedTuple` so that the returned object is not affected by changes to the parent data frame of which `dfr` is a view.
