```
scatter_image(psm::AbstractPhaseScreen, imap::IntensityMap; νref::Number = c_cgs, noise_screen=nothing, rng = Random.default_rng(), use_approx::Bool=true)
```

# Arguments

  * `psm::AbstractPhaseScreen`: An instance of the phase screen.
  * `imap::IntensityMap`: An instance of the intensity map.

# Parameters

  * `νref::Number=c_cgs`: The frequency in Hz to be used to simulate scattering effects. If the frequency of the image is not provided, this value is used.
  * `noise_screen=nothing`: The noise screen to be used to generate the phase screen. If not provided, a gaussian noise screen is generated.
  * `rng = Random.default_rng()`: The random number generator.
  * `use_approx::Bool=true`: If true, the approximate analytic formula is used to compute the scattering kernel. Otherwise semi-analytic formula is used.
