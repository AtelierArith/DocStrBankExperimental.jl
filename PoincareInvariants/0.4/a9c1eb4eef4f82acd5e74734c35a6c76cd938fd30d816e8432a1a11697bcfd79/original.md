```
FirstPoincareInvariant{T, D}(θ::θT, N::Integer, plan::P)
```

constructs a `FirstPoincareInvariant` setup object to calculate integral invariants, given a numeric type `T`, a phase space dimension `D`, a differential form `θ`, a number of points `N` and a `plan`. Note that the number of points may not be exactly `N`. The true number used depends on the implementation and is guaranteed to be no smaller than `N` and not too much larger.
