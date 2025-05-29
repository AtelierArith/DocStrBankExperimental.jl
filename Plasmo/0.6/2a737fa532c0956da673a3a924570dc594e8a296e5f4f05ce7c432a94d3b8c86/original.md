```
JuMP.num_constraints(graph::OptiGraph; count_variable_in_set_constraints=true)
```

Return the total number of constraints in `graph`. If `count_variable_in_set_constraints` is set to true, this also includes variable bound constraints. 
