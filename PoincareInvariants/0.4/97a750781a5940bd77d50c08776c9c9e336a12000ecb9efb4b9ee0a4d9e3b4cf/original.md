```
FirstPoincareInvariant{T, D}(θ::θT, N::Integer, P::Type=DEFAULT_FIRST_PLAN)
```

constructs a `FirstPoincareInvariant` setup object to calculate integral invariants, given a numeric type `T`, a phase space dimension `D`, a differential form `θ`, a number of points `N` and a `plan` type `P`, to be initialised and used for future computation.

The plan type defaults to `DEFAULT_FIRST_PLAN`, which is currently set to `FirstFourierPlan`.
