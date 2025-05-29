```
summarize_table(::Val{:hours})
```

| column_name | data_type | unit       | required | description                          |
|:----------- |:--------- |:---------- |:-------- |:------------------------------------ |
| `hours`     | Float64   | E4ST.Hours | true     | 各代表的な時間に費やされた時間の合計（8760に合計する必要があります） |
