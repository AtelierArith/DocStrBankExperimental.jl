```
resample(x::AbstractVector, rate::Real[, coef::Vector])
```

Resample `x` at rational or arbitrary `rate`. `coef` is an optional vector of FIR filter taps. If `coef` is not provided, the taps will be computed using a Kaiser window.

Internally, `resample` uses a polyphase `FIRFilter` object, but performs additional operations to make resampling a signal easier. It compensates for the `FIRFilter`'s delay (ramp-up), and appends zeros to `x`. The result is that when the input and output signals are plotted on top of each other, they correlate very well, but one signal will have more samples than the other.
