```
(N, ωn) = buttord(Wp::Tuple{Real,Real}, Ws::Tuple{Real,Real}, Rp::Real, Rs::Real; domain=:z)
```

Butterworth order estimate for bandpass and bandstop filter types.  `Wp` and `Ws` are 2-element pass  and stopband frequency edges, with no more than `Rp` dB passband ripple and at least `Rs` dB stopband  attenuation. Based on the ordering of passband and bandstop edges,  the Bandstop or Bandpass filter  type is inferred. `N` is an integer indicating the lowest estimated filter order, with `ωn` specifying the cutoff or "-3 dB" frequencies. If a domain of `:s` is specified, the passband and stopband frequencies  are interpretted as radians/second, giving an order and natural frequencies for an analog filter. The default domain is `:z`, interpretting the input frequencies as normalized from 0 to 1, where 1 corresponds to π radians/sample.
