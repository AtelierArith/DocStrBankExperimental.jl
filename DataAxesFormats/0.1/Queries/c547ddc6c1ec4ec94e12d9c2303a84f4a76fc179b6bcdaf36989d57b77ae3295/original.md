```
q"..."
```

Shorthand for parsing a literal string as a [`Query`](@ref). This is equivalent to [`Query`](@ref)`(raw"...")`, that is, a `\` can be placed in the string without escaping it (except for before a `"`). This is very convenient for literal queries (e.g., `q"/ cell = ATCG\:B1 : batch"` == `Query(raw"/ cell = ATCG\:B1 : batch")` == `Query("/ cell = ATCG\\:B1 : batch")` == `Axis("cell") |> IsEqual("ATCG:B1") |> Lookup("batch")).
