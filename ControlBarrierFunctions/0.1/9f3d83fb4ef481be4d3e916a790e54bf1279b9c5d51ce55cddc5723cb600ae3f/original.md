```
TunableQPSafetyFilter <: SafetyFilter
```

Controller that solves a control barrier function-based quadratic program (CBF-QP) with tunable class K functions.

Uses OSQP to solve the corresponding QP.

# Fields

  * `k::Function` : function that computes safe control actions
