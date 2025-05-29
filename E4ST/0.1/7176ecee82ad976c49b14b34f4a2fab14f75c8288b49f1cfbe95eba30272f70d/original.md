```
summarize_table(::Val{:af_table})
```

| column_name | data_type       | unit                            | required | description                                                                                                      |
|:----------- |:--------------- |:------------------------------- |:-------- |:---------------------------------------------------------------------------------------------------------------- |
| `area`      | AbstractString  | E4ST.NA                         | true     | The area with which to filter by. I.e. "state". Leave blank to not filter by area.                               |
| `subarea`   | AbstractString  | E4ST.NA                         | true     | The subarea to include in the filter.  I.e. "maryland".  Leave blank to not filter by area.                      |
| `genfuel`   | AbstractString  | E4ST.NA                         | true     | The fuel type that the generator uses. Leave blank to not filter by genfuel.                                     |
| `gentype`   | String          | E4ST.NA                         | true     | The generation technology type that the generator uses. Leave blank to not filter by gentype.                    |
| `year`      | E4ST.YearString | E4ST.Year                       | false    | The year to apply the AF's to, expressed as a year string prepended with a "y".  I.e. "y2022"                    |
| `status`    | Bool            | E4ST.NA                         | false    | Whether or not to use this AF adjustment                                                                         |
| `h_`        | Float64         | E4ST.MWhGeneratedPerMWhCapacity | true     | Availability factor of hour _.  Include 1 column for each hour in the hours table.  I.e. `:h1`, `:h2`, ... `:hn` |
