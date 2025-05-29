```
dof(path::RegularizationPath)
```

Approximates the degrees-of-freedom in each segment of the path as the number of non zero coefficients plus a dispersion parameter when appropriate. Note that for GammaLassoPath this may be a crude approximation, as gamlr does this differently.
