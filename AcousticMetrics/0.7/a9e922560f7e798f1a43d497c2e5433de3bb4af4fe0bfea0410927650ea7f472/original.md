```
MSPSpectrumAmplitude(pth::AbstractPressureTimeHistory, istonal::Bool=false, hc=similar(pressure(pth)))
```

Construct a narrowband spectrum of the mean-squared pressure amplitude from a pressure time history.

The optional argument `hc` will be used to store the discrete Fourier transform of the pressure time history, and should have length of `inputlength(pth)`. The `istonal` `Bool` argument, if `true`, indicates the pressure spectrum is tonal and thus concentrated at discrete frequencies. If `false`, the spectrum is assumed to be constant over each frequency band.
