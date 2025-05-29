```
ensembleaverage(sm::AbstractScatteringModel, skymodel::AbstractModel, νmodel; use_approx=true)
```

Compute the ensemble-average image of the input skymodel `skymodel` using the scattering model `sm`.

# Arguments

  * `sm::AbstractScatteringModel`: An instance of the scattering model.
  * `skymodel::AbstractModel`: An instance of `AbstractModel`.
  * `νmodel::Number=c_cgs`: The frequency in Hz to compute the scattering kernel.
  * `use_approx::Bool=true`: If true, the approximate analytic formula is used to compute the scattering kernel. Otherwise semi-analytic formula is used.
