```
Nystrom4
```

A 4th order explicit Runge-Kutta-Nyström method which can be applied directly on second order ODEs. Can only be used with fixed time steps.

In case the ODE Problem is not dependent on the first derivative consider using [`Nystrom4VelocityIndependent`](@ref) to increase performance.

## References

E. Hairer, S.P. Norsett, G. Wanner, (1993) Solving Ordinary Differential Equations I. Nonstiff Problems. 2nd Edition. Springer Series in Computational Mathematics, Springer-Verlag.
