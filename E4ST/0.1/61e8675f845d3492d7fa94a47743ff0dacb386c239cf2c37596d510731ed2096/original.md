```
summarize_table(::Val{:fuel_price})
```

| column_name | data_type | unit                 | required | description                                                                                                                  |
|:----------- |:--------- |:-------------------- |:-------- |:---------------------------------------------------------------------------------------------------------------------------- |
| `genfuel`   | String    | E4ST.NA              | true     | The type of fuel that the price applies for. i.e. `ng` or `coal`                                                             |
| `area`      | String    | E4ST.NA              | true     | The area that the price applies for i.e. `nation`.  Leave blank if grid-wide                                                 |
| `subarea`   | String    | E4ST.NA              | true     | The subarea that the price applies for i.e. `narnia`.  Leave blank if grid-wide                                              |
| `filter_`   | String    | E4ST.NA              | false    | I.e. `filter1`, `filter2`, etc. Other filter conditions that the price applies for, see [`parse_comparison`](@ref) for ideas |
| `price`     | Float64   | E4ST.DollarsPerMMBtu | true     | The price of 1 MMBtu of fuel                                                                                                 |
| `quantity`  | Float64   | E4ST.MMBtu           | true     | The number of MMBtu of the fuel available at the price in each year.  Set to `Inf` for unlimited.                            |
