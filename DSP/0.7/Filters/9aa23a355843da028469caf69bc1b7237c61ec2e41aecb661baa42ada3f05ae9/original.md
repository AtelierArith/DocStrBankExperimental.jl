```
FIRWindow(; transitionwidth, attenuation=60, scale=true)
```

Kaiser window FIR filter design. The required number of taps is calculated based on `transitionwidth` (in half-cycles/sample) and stopband `attenuation` (in dB). `attenuation` defaults to 60 dB.
