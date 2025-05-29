```
is_axis_query(query::QueryString)::Bool
```

Returns whether the `query` specifies a (possibly masked) axis. This also verifies the query is syntactically valid, though it may still fail if applied to specific data due to invalid data values or types.
