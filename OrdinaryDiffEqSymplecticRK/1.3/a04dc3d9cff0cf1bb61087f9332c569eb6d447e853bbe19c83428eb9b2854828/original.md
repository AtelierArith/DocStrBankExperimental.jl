```julia
LeapfrogDriftKickDrift()
```

Symplectic Runge-Kutta Methods 2nd order explicit symplectic integrator. Drift-kick-drift form of `VerletLeapfrog` designed to work when `f1` depends on `v`. Requires two evaluation of `f1` per step.

### Keyword Arguments

## References

@article{monaghan2005, 	title = {Smoothed particle hydrodynamics}, 	author = {Monaghan, Joseph J.}, 	year = {2005}, 	journal = {Reports on Progress in Physics}, 	volume = {68}, 	number = {8}, 	pages = {1703–1759}, 	doi = {10.1088/0034-4885/68/8/R01}, }
