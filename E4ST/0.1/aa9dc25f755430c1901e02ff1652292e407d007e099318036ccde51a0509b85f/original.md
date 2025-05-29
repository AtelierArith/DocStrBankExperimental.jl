```
get_table(data, table_name, conditions...) -> subtable::SubDataFrame
```

Return a subset of the table `table_name` for which the row passes the `conditions`.  Conditions are `Pair`s generally consisting of `<column name> => value`.  Here are some examples of supported conditions:

  * `:genfuel => "ng"` - All rows for which `row.genfuel == "ng"`
  * `"bus_idx" => 1` - All rows for which `row.bus_idx == 1`.  Note that the column name can be String or Symbol
  * `:bus_idx  => "1"` - All rows for which `row.bus_idx == 1`.  Note that this is a String but it will get converted to the eltype of table.bus_idx for the comparison
  * `:year_on  => ("y2022", "y2030")` - All rows for which `row.year_on` is between "y2022" and "y2030", inclusive.  Also works for fractional years.
  * `:genfuel => ["ng", "solar", "wind"]` - All rows for which `row.genfuel` is either "ng", "solar", or "wind"
  * `:emis_co2 => f::Function` - All rows for which f(row.emis_co2) returns `true`.  For example `>(0)`, or `x->(0<x<=0.5)`
