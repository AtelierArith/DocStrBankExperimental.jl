```
PressureSpectrumAmplitude(hc, dt, t0=zero(dt), istonal::Bool=false)
```

Construct a narrowband spectrum of the pressure amplitude from the discrete Fourier transform in half-complex format `hc`, time step size `dt`, and initial time `t0`. The `istonal` `Bool` argument, if `true`, indicates the pressure spectrum is tonal and thus concentrated at discrete frequencies. If `false`, the spectrum is assumed to be constant over each frequency band.
