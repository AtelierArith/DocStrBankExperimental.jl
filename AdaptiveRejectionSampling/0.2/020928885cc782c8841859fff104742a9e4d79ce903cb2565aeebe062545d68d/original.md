```
Objective(logf::Function, support:)
Objective(logf::Function, grad::Function)
```

Convenient structure to store the objective function to be sampled. It must receive the logarithm of f and not f directly. It uses automatic differentiation by default, but the user can provide the derivative optionally.
