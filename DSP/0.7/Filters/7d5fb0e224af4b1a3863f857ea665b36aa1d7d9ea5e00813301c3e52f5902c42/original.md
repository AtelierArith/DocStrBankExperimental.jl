```
(N, ωn) = buttord(Wp::Real, Ws::Real, Rp::Real, Rs::Real; domain=:z)
```

LPF/HPF Butterworth filter order and -3 dB frequency approximation. `Wp` and `Ws` are  the passband and stopband frequencies, whereas Rp and Rs  are the passband and stopband  ripple attenuations in dB. If the passband is greater than stopband, the filter type  is inferred to be for estimating the order of a highpass filter. `N` specifies the lowest possible integer filter order, whereas `ωn` is the cutoff or "-3 dB" frequency. If a domain  of `:s` is specified, the passband and stopband edges are interpretted as radians/second,  giving an order and natural frequency result for an analog filter. The default domain  is `:z`, interpretting the input frequencies as normalized from 0 to 1, where 1 corresponds  to π radians/sample.
