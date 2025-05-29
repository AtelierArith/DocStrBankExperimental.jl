linearfitxy(X, Y; σX=0, σY=0, r=0, isplot=false, ratio=1)

Performs 1D linear fitting of experimental data with uncertainties in  X and Y:

  * Linear fit:             `Y = a + b*X`                               [1]
  * Errors:                 $X ± σX;  Y ± σY$                         [2]
  * Errors' correlation:    $r =  = cov(σX, σY) / (σX * σY)$          [3]

# Arguments:

  * `X` and `Y` are input data vectors with length ≥ 3
  * Optional standard deviation errors $σX$ and $σY$ are vectors or scalars
  * Optional `r` is the correlation between the $σX$ and $σY$ errors

`r` can be a vector or scalar

$σX$ and $σY$ errors (error ellipses) with bivariate Gaussian distribution assumed. If no errors, or if only $σX$ or $σY$ are provided, then the results are equivalent to those from the [LsqFit.jl](https://github.com/JuliaNLSolvers/LsqFit.jl) package.

Based on York et al. (2004) with extensions (confidence intervals, diluted corr. coeff.).

# Examples:

```julia-repl
st = linearfitxy(X, Y)    # no errors in X and Y, no plot displayed

st = linearfitxy(X, Y; σX, σY, isplot=true) # XY errors not correlated (r=0); plot ratio=1

linearfitxy(X, Y; σX,σY,r=0,isplot=true,ratio=:auto) # XY errors not correlated (r=0); plot
```

The results are in the fields of the returned st::stfitxy structure:

  * The intercept `a`, the slope `b` and their uncertainties `σa` and `σb`
  * $σa95$ and $σb95$: 95%-confidence interval using two-tailed t-Student distribution,   e.g.: $b ± σb95 = b ± t(0.975,N-2)*σb$
  * Goodness of fit `S` (reduced $Χ²$ test): quantity with $Χ²$ N-2 degrees of freedom `S ~ 1`: fit consistent with errors, `S > 1`: poor fit, `S >> 1`: errors underestimated, `S < 1`: overfitting or errors overestimated
  * Pearson's correlation coefficient $ρ$ that accounts for data errors
  * Optional display of fit results with error ellipses and confidence intervals

The default argument `isplot=false` can be turned on to plot the results. Currently Plots.jl's gr() is used
