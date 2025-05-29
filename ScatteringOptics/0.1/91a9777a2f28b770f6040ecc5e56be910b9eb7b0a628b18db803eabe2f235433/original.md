```
ensembleaverage(sm::AbstractScatteringModel, imap::IntensityMap; νref=c_cgs, use_approx=true)
```

Compute the ensemble-average image of the input intensity map `imap` using the scattering model `sm`. The frequency of the image, if exists in its metadata, is used to compute the scattering kernel.  Otherwise `νref` is used to compute the scattering kernel.

# Arguments

  * `sm::AbstractScatteringModel`: An instance of the scattering model.
  * `imap::IntensityMap`: An instance of the intensity map.
  * `νref::Number=c_cgs`: The frequency in Hz to compute the scattering kernel.
  * `use_approx::Bool=true`: If true, the approximate analytic formula is used to compute the scattering kernel. Otherwise semi-analytic formula is used.
