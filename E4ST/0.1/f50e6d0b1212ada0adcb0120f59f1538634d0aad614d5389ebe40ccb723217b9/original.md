```
summarize_table(::Val{:load_match})
```

| column_name | data_type | unit         | required | description                                                                                                                                                                                                                |
|:----------- |:--------- |:------------ |:-------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `area`      | String    | E4ST.NA      | true     | The area with which to filter by. I.e. "state". Leave blank to not filter by area.                                                                                                                                         |
| `subarea`   | String    | E4ST.NA      | true     | The subarea to include in the filter.  I.e. "maryland".  Leave blank to not filter by area.                                                                                                                                |
| `load_type` | String    | E4ST.NA      | false    | The type of load represented for this load match.  Leave blank to not filter by type.                                                                                                                                      |
| `status`    | Bool      | E4ST.NA      | false    | Whether or not to use this match                                                                                                                                                                                           |
| `y_`        | Float64   | E4ST.MWhLoad | true     | The annual load energy to match for the weighted load of all load elements in the loads specified.  Include 1 column for each year being simulated.  I.e. "y2030", "y2035", ... To not match a specific year, make it -Inf |
