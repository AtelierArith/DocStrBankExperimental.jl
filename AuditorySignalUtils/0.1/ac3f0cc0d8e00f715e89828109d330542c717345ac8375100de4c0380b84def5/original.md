```
sam_noise(; kwargs...)
```

Synthesize sinusoidally amplitude-modulated noise with mod freq `fm` and depth `m`

Synthesizes a bandlimited Gaussian noise carrier using `gaussian_noise` (additional  unspecified keyword arguments are passed to `gaussian_noise`, and can thus be used to  control the bandwidth or filters used in synthesizing the noise) and then modulates it using a sinusoidal modulator. Here, `level` is the overall level in dB SPL after modulation.

# Arguments

  * `fm=10.0`: Modulation rate (Hz)
  * `ϕ=-π/2`: Modulation phase (radians)
  * `m=1.0`: Modulation depth (a.u.)
  * `dur=1.0`: Total duration, including ramps (s)
  * `dur_ramp=0.01`: Ramp duration (s)
  * `level=50.0`: Overall level after modulation (dB SPL)
  * `fs=100e3`: Sampling rate (Hz)
