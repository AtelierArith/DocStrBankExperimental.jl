```
kerr_propagation(ψ₀,xs,ys,zs,total_steps;k=1,g=1)
```

Solve `∇² ψ + 2ik ∂_z ψ = - g |ψ|² ψ` under the initial condition `ψ₀`.

`xs` and `ys` are the grids over which `ψ₀` is calculated.

The outputs are saved at every `zs`, which is a number or a collection of numbers.

`total_steps` is the number of steps over which we discretize the propagation. The larger the `total_steps`, the better the precision and the slower is the calculation.
