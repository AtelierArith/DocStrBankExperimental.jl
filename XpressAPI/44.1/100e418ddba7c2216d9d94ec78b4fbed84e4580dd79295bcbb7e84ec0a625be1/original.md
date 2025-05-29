```
XPRS_PRIMALPERTURB
```

The factor by which the problem will be perturbed prior to optimization by primal simplex. (double)

A value of `0.0` results in no perturbation prior to optimization. Note the interconnection to the AUTOPERTURB control. If AUTOPERTURB is set to `1`, the decision whether to perturb or not is left to the Optimizer. When the problem is automatically perturbed in primal simplex, however, the value of PRIMALPERTURB will be used for perturbation.

Default value: `-1` determined automatically.

Domain: -1,[0,+INF]
