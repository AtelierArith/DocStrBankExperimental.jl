```
scale_constraints!(EP::Model, scaling_settings::ScalingSettings=ScalingSettings())
```

Scale the coefficients and RHS of all constraints in the model `EP` using the scaling settings `scaling_settings`. This function creates an array of all constraints in `EP` and then broadcasts scale*constraint!(con*ref, scaling_settings) on the array.
