```
XPRS_MIPCONCURRENTNODES
```

Sets the node limit for when a winning solve is selected when concurrent MIP solves are enabled. (integer)

When multiple MIP solves are started, they each run up to the `MIPCONCURRENTNODES` node limit and only one winning solve is selected for contuinuing the search with.

Default value: `-1`

Values: -1 : Automatic - let the solver decide on a node limit.

> 0


: Number of nodes each concurrent solve should complete before a winner is selected.
