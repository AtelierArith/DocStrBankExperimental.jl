```
struct WelfareTable <: Modification
```

Outputs a table with a breakdown of each of the terms going into welfare, for each year.

Arguments/keyword arguments:

  * name::Symbol
  * groupby - empty by default to not group by anything.  Could choose to group by state, county, etc.
