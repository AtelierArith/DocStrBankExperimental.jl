```
CreditByBenchmark(;gen_col, benchmark)
```

Awards credit of each generator based on how that generator's `gen_col` compares to `benchmark`, using the following formula.

```
max(1.0 - (gen_row[gen_col] / benchmark), 0.0)
```

  * `gen_col::Symbol` - the column of the `gen` table to compare against
  * `benchmark::Float64` - the benchmark rate to compare with, in the same units as the `gen_col`.
