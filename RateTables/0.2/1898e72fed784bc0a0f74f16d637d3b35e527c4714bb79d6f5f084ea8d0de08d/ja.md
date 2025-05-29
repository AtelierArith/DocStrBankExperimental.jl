```
daily_hazard(rt::BasicRateTable, age, date)
daily_hazard(rt::RateTable,      age, date, args...)
daily_hazard(rt::RateTable,      age, date; kwargs...)
```

この関数は、指定された BasicRateTable から日次ハザード値を照会します。パラメータ `age` と `date` は日数で指定する必要があります（1 年 = 365.241 日）。潜在的な args と kwargs は、レートテーブルをサブセットするために使用されます。
