```
normalize(df::DataFrame, normalizer::DataFrame; id = [:Analyte, :L], stats = (All(), "Accuracy"), colstats = :Stats)
```

Normalize `DataFrame` by the given normalizer.

# Arguments

  * `normalizer`: the `DataFrame` to normalize `df`.
  * `df`: the `DataFrame` to be normalized.
  * `id`: the column(s) (Symbol, string or integer) with a unique key for each row.
  * `stats`: a `Tuple` represented as statistics involved in normalization. The first argument applies to `df`, and the second applies to `normalizer`. `All()` indicates including all statistics.
  * `colstats`: column name of statistics.
