```
Nystrom4VelocityIdependent
```

A 4th order explicit Runkge-Kutta-Nyström method. Used directly on second order ODEs, where the acceleration is independent from velocity (ODE Problem is not dependent on the first derivative).

More efficient then [`Nystrom4`](@ref) on velocity independent problems, since less evaluations are needed.

Fixed time steps only.

## References

E. Hairer, S.P. Norsett, G. Wanner, (1993) Solving Ordinary Differential Equations I. Nonstiff Problems. 2nd Edition. Springer Series in Computational Mathematics, Springer-Verlag.
