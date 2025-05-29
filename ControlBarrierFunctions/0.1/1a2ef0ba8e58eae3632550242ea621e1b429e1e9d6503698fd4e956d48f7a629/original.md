```
ExplicitSafetyFilter <: SafetyFilter
```

Controller that uses the closed-form solution to a control barrier function quadratic program.

# Fields

  * `k::Function` : function that computes safe control actions
