```
StepsizeCallback(; cfl::Real)
```

Set the time step size according to a CFL condition if the time integration method isn't adaptive itself.

The current implementation is using the simplest form of CFL condition, which chooses a time step size that is constant during the simulation. The step size is therefore only applied once at the beginning of the simulation.

The step size $\Delta t$ is chosen as the minimum

$$
    \Delta t = \min(\Delta t_\eta, \Delta t_a, \Delta t_c),
$$

where

$$
    \Delta t_\eta = 0.125 \, h^2 / \eta, \quad \Delta t_a = 0.25 \sqrt{h / \lVert g \rVert},
    \quad \Delta t_c = \text{CFL} \, h / c,
$$

with $\nu = \alpha h c / (2n + 4)$, where $\alpha$ is the parameter of the viscosity and $n$ is the number of dimensions.

!!! warning "Experimental implementation"
    This is an experimental feature and may change in future releases.


## References

[Antuono2012](@cite), [Adami2012](@cite), [Sun2017](@cite), [Antuono2015](@cite)
