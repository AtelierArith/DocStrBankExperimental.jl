```
summarize_table(::Val{:interface_limit})
```

| column_name        | data_type | unit                   | required | description                                                                                                                                    |
|:------------------ |:--------- |:---------------------- |:-------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`             | String    | E4ST.NA                | false    | Name of the interface limit, not used                                                                                                          |
| `description`      | String    | E4ST.NA                | false    | Description of the interface limit, not used.                                                                                                  |
| `f_filter`         | String    | E4ST.NA                | true     | The filter for the bus table specifiying the region the power is flowing **f**rom.  I.e. `nation=>narnia`, or `state=>[angard, stormness]`     |
| `t_filter`         | String    | E4ST.NA                | true     | The filter for the bus table specifiying the region the power is flowing **t**o.                                                               |
| `pflow_max`        | Float64   | E4ST.MWFlow            | false    | The maximum allowable power flow in the direction of `f` to `t`. If left as ±Inf, no constraint made.                                          |
| `pflow_min`        | Float64   | E4ST.MWFlow            | false    | The minimum allowable power flow in the direction of `f` to `t`.  Can be positive or negative.  If left as ±Inf, no constraint made.           |
| `eflow_yearly_max` | Float64   | E4ST.MWhFlow           | false    | The yearly maximum allowable energy to flow in the direction of `f` to `t`. If left as ±Inf, no constraint made.                               |
| `eflow_yearly_min` | Float64   | E4ST.MWhFlow           | false    | The yearly minimum allowable energy to flow in the direction of `f` to `t`.  Can be positive or negative. If left as ±Inf, no constraint made. |
| `price`            | Float64   | E4ST.DollarsPerMWhFlow | false    | The price of net flow in the direction of `f` to `t`.                                                                                          |
| `include_dc`       | Bool      | E4ST.NA                | false    | Whether or not to include DC lines in this interface limit.  If not provided, assumed that DC lines are not included                           |
