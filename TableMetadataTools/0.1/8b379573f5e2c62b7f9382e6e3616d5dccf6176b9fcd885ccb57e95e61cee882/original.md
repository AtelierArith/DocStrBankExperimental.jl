```
findlabels(predicate, table)
```

Return a vector of column*name => column*label pairs containing all values for which `predicate(label(table, column_name))` returns `true`. This is intended for a quick lookup of column names whose label meets some criteria defined by `predicate`.

See also: [`label`](@ref), [`label!`](@ref), [`labels`](@ref)
