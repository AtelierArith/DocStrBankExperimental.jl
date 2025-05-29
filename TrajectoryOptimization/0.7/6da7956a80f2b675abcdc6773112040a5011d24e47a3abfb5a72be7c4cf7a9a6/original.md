```
rollout!(::Problem)
```

Simulate the dynamics forward from the initial condition `x0` using the controls in the trajectory `Z`. If a problem is passed in, `Z = prob.Z`, `model = prob.model`, and `x0 = prob.x0`.
