```
summarize_table(::Val{:reserve_requirements})
```

| column_name | data_type | unit       | required | description                                                   |
|:----------- |:--------- |:---------- |:-------- |:------------------------------------------------------------- |
| `subarea`   | Any       | E4ST.NA    | true     | 要件が指定されているサブエリア                                               |
| `y_`        | Float64   | E4ST.Ratio | true     | 負荷に対する予備容量のパーセント要件。時間テーブルの各年の列を含めます。すなわち、`:y2020`、`:y2030`など。 |
