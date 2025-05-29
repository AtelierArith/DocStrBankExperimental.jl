```julia
tMinDistMetropolis(smpl::ChronAgeData, nsteps::Int, burnin::Int, dist::Array{Float64})
```

Calculate the minimum limiting (eruption/deposition) age of each sample defined in the `smpl` struct, using the `Isoplot.metropolis_min` function, assuming mineral ages for each sample are drawn from the source distribution `dist`. Fits a `BilinearExponential` function to the resulting stationary distribution for each sample and stores the results in `smpl.Params` for use by the `StratMetropolisDist` function.

If the samples provided as csv files in `smpl.Path` take the five-column form of U-Pb isotopic data files, these will be interpreted as the columns

```
| ²⁰⁷Pb/²³⁵U | uncert (absolute) | ²⁰⁶Pb/²³⁸U | uncert (absolute) | correlation |
```

and Pb-loss-aware eruption/deposition age estimation will be conducted. In all other cases, the first two columns of each data file will be interpreted as

```
| Age | Age uncert (absolute) |
```

and standard eruption/deposition age estimation will be conducted.

In all cases, uncertainties will be treated as one or two-sigma *absolute* based on the value of `smpl.inputSigmaLevel`.

### Examples

```julia
smpl = tMinDistMetropolis(smpl, 10^6, 10^5, HalfNormalDistribution)
```
