```julia
checkGradientsToleranceMask(fgc; ...)
checkGradientsToleranceMask(fgc, J; tol)

```

Return a mask of same size as gradients matrix `J`, indicating which elements are above the expected sensitivity threshold `tol`.

Notes

  * Threshold accuracy depends on two parts,

      * Numerical gradient perturbation size `fgc._h`,
      * Accuracy tolerance to which the factor residual is computed (not controlled here)
