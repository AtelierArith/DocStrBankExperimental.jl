```
(N, ωn) = cheb1ord(Wp::Real, Ws::Real, Rp::Real, Rs::Real; domain::Symbol=:z)
```

Integer and natural frequency order estimation for Chebyshev Type I Filters. `Wp` and `Ws` indicate the passband and stopband frequency edges, and `Rp` and `Rs` indicate the maximum loss in the passband and the minimum attenuation in the stopband, (in dB.) Based on the ordering of passband and stopband edges, the Lowpass or Highpass filter type is inferred. `N` indicates the smallest integer filter order that achieves the desired specifications, and `ωn` contains the natural frequency of the filter, (in this case, simply the passband edge.) If a domain of `:s` is specified, the passband and stopband edges are interpretted as radians/second, giving an order and natural frequency result for an analog filter. The default domain is `:z`, interpretting the input frequencies as normalized from 0 to 1, where 1 corresponds to π radians/sample.
