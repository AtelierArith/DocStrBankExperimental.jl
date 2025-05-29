```
set_to_node_objectives(graph::OptiGraph)
```

Set the `graph` objective to the summation of all of its optinode objectives. Assumes the  objective sense is an MOI.MIN_SENSE and accounts for the sense of node objectives  accordingly. 

Note that building nonlinear objective functions is much slower than  linear or quadratic because nonlienar expressions cannot be updated in place.
