```
JuMP.add_constraint(node::OptiNode, con::JuMP.AbstractConstraint, name::String="")
```

Add a constraint `con` to optinode `node`. This function supports use of the @constraint  JuMP macro.
