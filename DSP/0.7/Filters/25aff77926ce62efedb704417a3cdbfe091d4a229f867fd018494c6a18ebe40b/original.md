```
FIRWindow(window; scale=true)
```

FIR filter design using window `window`, a vector whose length matches the number of taps in the resulting filter.

If `scale` is `true` (default), the designed FIR filter is scaled so that the following holds:

  * For [`Lowpass`](@ref) and [`Bandstop`](@ref) filters, the frequency response is unity at 0 (DC).
  * For [`Highpass`](@ref) filters, the frequency response is unity at the Nyquist frequency.
  * For [`Bandpass`](@ref) filters, the frequency response is unity in the center of the passband.
