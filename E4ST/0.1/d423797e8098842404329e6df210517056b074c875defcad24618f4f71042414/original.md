```
get_credit(c::CreditByBenchmark, data, gen_row::DataFrameRow) ->
```

Returns the credit level based on the formula `max(1.0 - (gen_row[gen_col] / c.benchmark), 0.0)`. 
