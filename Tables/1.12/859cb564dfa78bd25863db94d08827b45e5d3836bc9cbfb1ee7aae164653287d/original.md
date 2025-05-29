```
Tables.schema(x) => Union{Nothing, Tables.Schema}
```

Attempt to retrieve the schema of the object returned by `Tables.rows` or `Tables.columns`. If the `AbstractRow` iterator or `AbstractColumns` object can't determine its schema, `nothing` will be returned. Otherwise, a `Tables.Schema` object is returned, with the column names and types available for use.
