```
flux_nonconservative_chan_etal(u_ll, u_rr, orientation::Integer,
                               equations::CompressibleEulerEquationsQuasi1D)
flux_nonconservative_chan_etal(u_ll, u_rr, normal_direction, 
                               equations::CompressibleEulerEquationsQuasi1D)
flux_nonconservative_chan_etal(u_ll, u_rr, normal_ll, normal_rr,
                               equations::CompressibleEulerEquationsQuasi1D)
```

Non-symmetric two-point volume flux discretizing the nonconservative (source) term that contains the gradient of the pressure  [`CompressibleEulerEquationsQuasi1D`](@ref)  and the nozzle width.

Further details are available in the paper:

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)   High order entropy stable schemes for the quasi-one-dimensional   shallow water and compressible Euler equations   [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
