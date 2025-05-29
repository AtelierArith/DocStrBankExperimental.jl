```
get_query(
    daf::DafReader,
    query::QueryString;
    [cache::Bool = true]
)::Union{StorageScalar, NamedVector, NamedMatrix}
```

Apply the full `query` to the `Daf` data and return the result. By default, this will cache results, so repeated queries will be accelerated. This may consume a large amount of memory. You can disable it by specifying `cache = false`, or release the cached data using [`empty_cache!`](@ref).

As a shorthand syntax you can also invoke this using `getindex`, that is, using the `[]` operator (e.g., `daf[q"/ cell"]` is equivalent to `get_query(daf, q"/ cell")`).
