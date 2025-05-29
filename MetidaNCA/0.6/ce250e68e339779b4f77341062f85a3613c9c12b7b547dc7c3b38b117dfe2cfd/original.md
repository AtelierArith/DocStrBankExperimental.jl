```
pdimport(data, time, obs, sort;
    bl = 0,
    th = 0,
    limitrule::Union{Nothing, LimitRule} = nothing,
    warn = true)
```

Import pharmackodynamic data from table:

  * `data` - data table;
  * `time` - observation time;
  * `obs` - observation value;
  * `sort` - sorting columns.

Keywords:

  * `bl` - baseline;
  * `th` - threshold;
  * `limitrule` - limit rule;
  * `warn` - warning supress if `false`.
