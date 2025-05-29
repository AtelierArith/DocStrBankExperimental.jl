```
struct YearlyTable <: Modification

YearlyTable(;name, table_name, groupby=Symbol[], group_hours_by=Symbol[])
```

This modification creates an agregated table for each year in the simulation.  It includes all of the result formulas listed in [`get_results_formulas(data, table_name)`](@ref), grouped by column names in `groupby`.  The hours are grouped by columns from the `group_hours_by` field.

# Fields:

  * `name` - the name of the Modification, (don't need to specify this field in config file).  The outputed table will be saved to [`get_out_path(config, "<name>_<year>.csv")`](@ref)
  * `table_name` - the name of the table to export.  I.e. `gen`, `bus`, or `branch`
  * `groupby = Symbol[]` - the name(s) of the columns of the table specified by `table_name` to group by. I.e. `state`, `nation`, `genfuel`, `gentype`, etc.  Leave blank to group the whole table together into a single row.  To prevent any grouping and show every row, give a `:`
  * `group_hours_by = Symbol[]` - the name(s) of the columns of the hours table to group by.  I.e. `season`.  Leave blank to group the whole table together. To prevent any grouping and show every hour, give a `:`
