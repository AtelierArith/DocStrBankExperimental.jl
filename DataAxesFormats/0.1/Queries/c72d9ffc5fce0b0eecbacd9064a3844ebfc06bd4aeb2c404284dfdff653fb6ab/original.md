```
query_result_dimensions(query::QueryString)::Int
```

Return the number of dimensions (-1 - names, 0 - scalar, 1 - vector, 2 - matrix) of the results of a `query`. This also verifies the query is syntactically valid, though it may still fail if applied to specific data due to invalid data values or types.
