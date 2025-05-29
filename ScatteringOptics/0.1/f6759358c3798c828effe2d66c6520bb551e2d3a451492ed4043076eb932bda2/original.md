```
phase_screen(psm::AbstractPhaseScreen, λ_cm, noise_screen=nothing)
```

Generates a refractive phase screen, `ϕ`, using StationaryRandomFields.jl the power law noise procedure.  The fourier space 2D noise*screen (defaults to gaussian noise screen if not given) is scaled by the power law, `Q`, defined in input AbstractPhaseScreen `psm`. The observing wavelength, `λ*cm`, must be given.
