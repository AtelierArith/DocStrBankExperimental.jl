```
@optinode(optigraph, expr...)
```

Add a new optinode to `optigraph`. The expression `expr` can either be

  * of the form `nodename` creating a single optinode with the variable name `varname`
  * of the form `nodename[...]` or `[...]` creating a container of optinodes using JuMP Containers
