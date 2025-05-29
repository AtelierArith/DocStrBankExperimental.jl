```
scale_constraints!(constraint_list::Vector{ConstraintRef}, scaling_settings::ScalingSettings=ScalingSettings())
```

Scale the coefficients and RHS of all constraints in the model `EP` using the scaling settings `scaling_settings`. This function calls scale*constraint!(con*ref, scaling*settings) on each constraint in `constraint*list`.
