```
JuMP.optimize!(model::GPModel)
```

Solves the geometric programming model by transforming it to a convex optimization problem in log space.

# Steps

1. Transforms the model to log space
2. Solves the transformed model using the specified optimizer
3. Maps the solution back to the original variables

# Throws

  * Error if no objective function is set
