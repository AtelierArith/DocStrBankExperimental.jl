```
Filter(pred)
```

Filters the table returning only the rows where the predicate `pred` is `true`.

# Examples

```julia
Filter(row -> sum(row) > 10)
Filter(row -> row.a == true && row.b < 30)
Filter(row -> row."a" == true && row."b" < 30)
Filter(row -> row[1] == true && row[2] < 30)
Filter(row -> row[:a] == true && row[:b] < 30)
Filter(row -> row["a"] == true && row["b"] < 30)
```

## Notes

  * The schema of the table is preserved by the transform.
