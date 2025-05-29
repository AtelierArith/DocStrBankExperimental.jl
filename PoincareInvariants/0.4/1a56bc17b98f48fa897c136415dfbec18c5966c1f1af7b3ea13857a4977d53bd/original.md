```
SecondPoincareInvariant{T, D}(ω, N, P::Type=DEFAULT_SECOND_PLAN)
```

constructs a `SecondPoincareInvariant` setup object to calculate integral invariants, given a numeric type `T`, a phase space dimension `D`, a differential form `ω`, a point specification `N` and a `plan` type `P`, to be initialised and used for future computation.

The plan type defaults to `DEFAULT_SECOND_PLAN`, which is currently set to `SecondChebyshevPlan`. Note that the number of points may not be exactly `N`. The true number used depends on the implementation and is guaranteed to be no smaller than `N` and not too much larger. For the `SecondFinDiffPlan`, the grid of points may also be specified as a tuple `(Nx, Ny)`, if non-square grids are sought.
