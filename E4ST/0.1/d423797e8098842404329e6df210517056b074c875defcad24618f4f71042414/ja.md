```
get_credit(c::CreditByBenchmark, data, gen_row::DataFrameRow) ->
```

クレジットレベルは、式 `max(1.0 - (gen_row[gen_col] / c.benchmark), 0.0)` に基づいて返されます。
