```
summarize_table(::Val{:genfuel})
```

| column_name | data_type      | unit    | required | description                                                              |
|:----------- |:-------------- |:------- |:-------- |:------------------------------------------------------------------------ |
| `gentype`   | String         | E4ST.NA | true     | The generator type (ie. ngcc, dist*solar, os*wind)                       |
| `genfuel`   | AbstractString | E4ST.NA | true     | The corresponding generator fuel or renewable type (ie. ng, solar, wind) |
