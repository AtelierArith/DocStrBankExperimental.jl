```
model, x0 = subspaceid(frd::FRD, Ts, args...; estimate_x0 = false, bilinear_transform = false, kwargs...)
```

If a frequency-reponse data object is supplied

  * The FRD will be automatically converted to an [`InputOutputFreqData`](@ref)
  * `estimate_x0` is by default set to 0.
  * `bilinear_transform` transform the frequency vector to discrete time, see note below.

Note: if the frequency-response data comes from a frequency-response analysis, a bilinear transform of the data is required before estimation. This transform will be applied if `bilinear_transform = true`.
