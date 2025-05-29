```
compute_drt(ω_exp,Z_exp;ppd,showplot,rtol,regularization)
```

Main function for computing the DRT from input EIS data.

# Attributes

  * `ω_exp`: Input EIS frequency
  * `Z_exp`: Input EIS Impedance
  * `ppd=7`: Points-per-decade in output τ range for computing DRT
  * `showplot=false`: Whether or not to plot DRT results
  * `rtol=1e-03`: The desired relative tolerance. Function outputs a warning if the fit result is above this
  * `regularization=false`: Whether or no to employ the regularization method

# Examples

```julia
using EISAnalysis, Statistics
eval(initialize())
ω_exp, Z_exp = (r/q).ω, (r/q).Z #replace this with real data
fit = compute_drt(ω_exp,Z_exp;showplot = false,regularization = true)
```
