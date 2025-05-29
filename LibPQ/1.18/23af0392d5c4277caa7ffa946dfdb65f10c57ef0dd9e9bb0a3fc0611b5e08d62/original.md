```
num_affected_rows(jl_result::Result) -> Int
```

Return the number of rows affected by the command returning the result. This is useful for counting the rows affected by operations such as INSERT, UPDATE and DELETE that do not return rows but affect them. This will be 0 if the query does not affect any row.
