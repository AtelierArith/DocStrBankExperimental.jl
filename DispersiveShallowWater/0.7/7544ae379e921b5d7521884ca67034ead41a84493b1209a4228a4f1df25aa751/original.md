```
initial_condition_discontinuous_well_balancedness(x, t, equations::AbstractShallowWaterEquations, mesh)
```

Setup a truly discontinuous bottom topography function for this academic lake-at-rest test case of well-balancedness, i.e. `eta` is constant and `v` is zero everywhere. The error for this lake-at-rest test case `∫|η-η₀|` should be around machine roundoff.
