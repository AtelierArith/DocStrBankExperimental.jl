```
summarize_table(::Val{:genfuel})
```

| column_name | data_type      | unit    | required | description                                |
|:----------- |:-------------- |:------- |:-------- |:------------------------------------------ |
| `gentype`   | String         | E4ST.NA | true     | 発電機の種類（例：ngcc、dist*solar、os*wind）          |
| `genfuel`   | AbstractString | E4ST.NA | true     | 対応する発電機の燃料または再生可能エネルギーの種類（例：ng、solar、wind） |
