```
JuMP.add_variable(node::OptiNode, v::JuMP.AbstractVariable, name::String="")
```

Add variable `v` to optinode `node`. This function supports use of the `@variable` JuMP macro. Optionally add a `base_name` to the variable for printing.
