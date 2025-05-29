```
 approx(psd_model, f0, fM, n_components=20, var=1.0; basis_function="SHO")
```

Approximate the PSD with a sum of basis functions to form a covariance function

# Arguments

  * `psd_model::PowerSpectralDensity`: model of the PSD
  * `f0::Real`: the lowest frequency
  * `fM::Real`: the highest frequency
  * `n_components::Integer=20`: the number of basis functions to use
  * `var::Real=1.0`: the variance of the process, integral of the PSD
  * `basis_function::String="SHO"`: the basis function to use, either "SHO" or "DRWCelerite"

# Return

  * `covariance::SumOfSemiSeparable`: the covariance function

# Example

```julia
using Pioran
𝓟 = SingleBendingPowerLaw(1.0, 1.0, 2.0)
𝓡 = approx(𝓟, 1e-4, 1e-1, 30, 2.31,basis_function="SHO")
```
