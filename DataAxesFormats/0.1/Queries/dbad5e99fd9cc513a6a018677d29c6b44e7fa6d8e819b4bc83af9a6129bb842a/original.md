```
query_requires_relayout(daf::DafReader, query::QueryString)::Bool
```

Whether computing the `query` for the `daf` data requires [`relayout!`](@ref) of some matrix. This also verifies the query is syntactically valid and that the query can be computed, though it may still fail if applied to specific data due to invalid values or types.
