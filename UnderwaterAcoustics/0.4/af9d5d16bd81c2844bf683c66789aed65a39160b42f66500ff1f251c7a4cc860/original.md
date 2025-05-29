```
PekerisModeSolver(env; ngrid=0)
```

A fast differentiable mode propagation model that only supports iso-velocity constant depth environments.

`ngrid` is the number of grid points to use for modal root finding for fluid bottom environments. If `ngrid` is too small, the mode solver may miss some modes. If `ngrid` is too large, the mode solver may take a long time to converge. The default value of `ngrid` of 0 will use a heuristic to automatically determine the number of grid points to use.
