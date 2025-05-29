```
JuMP.set_objective(
    graph::OptiGraph, 
    sense::MOI.OptimizationSense, 
    func::JuMP.AbstractJuMPScalar
)
```

Set the objective function and objective sense for `graph`. This method is called  internally when a user uses the `JuMP.@objective` macro.
