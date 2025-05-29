```
Simulation(model, frequency; kwargs...)
```

Create a simulation based on a propagation `model` with a nominal `frequency` (in Hz). The `model` is an 2½D or 3D acoustic propagation model compatible with `UnderwaterAcoustics.jl`.

Optional parameters:

  * `irate`: ADC frame rate for sampling acoustic signal (samples/s)
  * `iblksize`: ADC block size for streaming acoustic signal (samples, 0 for auto)
  * `orate`: DAC frame rate for transmitting acoustic signal (samples/s)
  * `txref`: Conversion between DAC input and acoustic source level (dB re µPa @ 1m)
  * `rxref`: Conversion between acoustic receive level and ADC output (dB re 1/µPa)
  * `noise`: Noise model for the simulation (default: RedGaussianNoise(1e6))

If `irate` is not specified, it defaults to 4 × `frequency`. If `orate` is not specified, it defaults to 8 × `frequency`.
