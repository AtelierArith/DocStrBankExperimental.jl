```
    ┌──────────────────────────────────────────────────────────────────────┐ 
0.2 │                              ▄▄▀▀▀▀▀▀▚▄▖                             │ 
    │                           ▗▞▀          ▝▀▄                           │ 
    │                         ▗▞▘               ▀▄                         │ 
    │                        ▄▘                   ▚▖                       │ 
    │                      ▗▀                      ▝▖                      │ 
    │                     ▞▘                        ▝▀▖                    │ 
    │                   ▄▀                            ▝▚▖                  │ 
    │                 ▗▞                                ▝▄                 │ 
    │                ▄▘                                   ▚▖               │ 
    │              ▗▞                                      ▝▄              │ 
    │            ▗▞▘                                         ▀▄            │ 
    │          ▗▞▘                                             ▀▄          │ 
    │        ▄▞▘                                                 ▀▄▖       │ 
    │     ▄▞▀                                                      ▝▀▄▖    │ 
  0 │ ▄▞▀▀                                                            ▝▀▀▄▖│ 
    └──────────────────────────────────────────────────────────────────────┘ 
    0                                                                     70


dpss(n::Integer, nw::Real, ntapers::Integer=iceil(2*nw)-1;
     padding::Integer=0, zerophase::Bool=false)
```

The first `ntapers` discrete prolate spheroid sequences (Slepian tapers) as an `n` × `ntapers` matrix. The signs of the tapers follow the convention that the first element of the skew-symmetric (odd) tapers is positive. The time-bandwidth product is given by `nw`.

The DPSS window maximizes the energy concentration in the main lobe.

If `zerophase` is `false` (the default) the window is centered around index `(n+1)/2`, which is commonly used for FIR filter design. These are often used for FIR filter design, and usually odd-length. Note that for even-length windows this will cause the window center to be located between samples.

If `zerophase` is `true` the window is centered around index 1 (with the negative half wrapped to the end of the vector). Additionally this creates a "periodic" window, which means that if there is no padding then the left and right endpoints of the window wrap around to the same sample, so the window length is the same as an `n+1`-length non-`zerophase` window. Alternatively you can think of the continuous `zerophase` window being of width `n` and the non-`zerophase` window being of length `n-1`. `zerophase` windows are often used in FFT processing, and are usually even-length.
