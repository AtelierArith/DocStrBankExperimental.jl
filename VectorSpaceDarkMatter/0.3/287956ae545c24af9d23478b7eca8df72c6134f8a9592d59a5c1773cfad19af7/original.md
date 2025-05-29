```
readFnlm(infile[, radial_basis::RadialBasis]; dict=false, use_err=true)
```

Reads coefficients from `infile`. Can optionally manually define the basis via `radial_basis` argument. Optional arguments:

`dict` : If `true`, will return an `FCoeffs`. If false, returns `ProjectedF`.

`use_err` : Whether or not to load the uncertainties on the `fnlm` values.
