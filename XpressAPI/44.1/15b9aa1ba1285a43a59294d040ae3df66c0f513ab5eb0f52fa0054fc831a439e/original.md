```
XPRS_BAROBJPERTURB
```

Defines how the barrier perturbs the objective. (double)

Default value: `1e-6`

Values:

> 0


: Let the optimizer decide if the objective is perturbed or not and use the parameter value as the scale of the perturbation. 0 : Turn off objective perturbation. <0 : Always perturb the objective by the absolute value of the parameter.
