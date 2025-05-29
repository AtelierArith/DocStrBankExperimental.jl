```
(N, ωn) = cheb2ord(Wp::Real, Ws::Real, Rp::Real, Rs::Real; domain::Symbol=:z)
```

Integer and natural frequency order estimation for Chebyshev Type II (inverse) Filters. `Wp` and `Ws` are the frequency edges for Bandpass/Bandstop cases, with `Rp` and `Rs` representing the ripple maximum loss in the passband and minimum ripple attenuation in the stopband in dB. Based on the ordering of the passband and stopband edges, the Lowpass or Highpass filter type is inferred. `N` is the integer indicating the lowest filter order, with `ωn` specifying the "-3 dB" cutoff frequency. If the domain is specified as `:s`, the passband and stopband frequencies are interpretted as radians/second, giving the order and natural frequencies for an analog filter. The default domain is `:z`, interpretting the input frequencies as normalized from 0 to 1, where 1 corresponds to π radians/sample.
