```
scatter_image(sm, imap::IntensityMap; νref::Number = c_cgs, Vx_km_per_s=0.0, Vy_km_per_s=0.0, rng = Random.default_rng(), use_approx::Bool=true)
```

Simulates the full interstellar scattering on an unscattered Comrade skymodel intensity map (`imap`). The frequency of the image, if exists in its metadata, is used to simulate the scattering effects. Otherwise `νref` is used.

# Arguments

  * `sm::AbstractScatteringModel`: An instance of the scattering model.
  * `imap::IntensityMap`: An instance of the intensity map.

# Parameters

  * `νref::Number=c_cgs`: The frequency in Hz to be used to simulate scattering effects. If the frequency of the image is not provided, this value is used.
  * `Vx_km_per_s=0.0`: The velocity of the observer in the x direction in km/s. (just placeholder for future implementation)
  * `Vy_km_per_s=0.0`: The velocity of the observer in the y direction in km/s. (just placeholder for future implementation)
  * `rng = Random.default_rng()`: The random number generator.
  * `use_approx::Bool=true`: If true, the approximate analytic formula is used to compute the scattering kernel. Otherwise semi-analytic formula is used.
