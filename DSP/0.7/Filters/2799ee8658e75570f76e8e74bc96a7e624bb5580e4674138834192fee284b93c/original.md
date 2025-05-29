```
(N, ωn) = cheb2ord(Wp::Tuple{Real, Real}, Ws::Tuple{Real, Real}, Rp::Real, Rs::Real; domain::Symbol=:z)
```

Integer and natural frequency order estimation for Chebyshev Type II (inverse) Filters. `Wp` and `Ws` are  2-element frequency edges for Bandpass/Bandstop cases, with `Rp` and `Rs` representing  the ripple maximum  loss in the passband and minimum ripple attenuation in the stopband in dB. Based on the ordering of passband  and bandstop edges, the Bandstop or Bandpass filter type is inferred. `N` is an integer indicating the  lowest estimated filter order, with `ωn` specifying the cutoff or "-3 dB" frequencies. If a domain of  `:s` is specified, the passband and stopband frequencies are interpretted as radians/second, giving an  order and natural frequencies for an analog filter. The default domain is `:z`, interpretting the input  frequencies as normalized from 0 to 1, where 1 corresponds to π radians/sample.
