```
flux_nonconservative_chan_etal(u_ll, u_rr, orientation::Integer,
                               equations::ShallowWaterEquationsQuasi1D)
flux_nonconservative_chan_etal(u_ll, u_rr, normal_direction::AbstractVector,
                               equations::ShallowWaterEquationsQuasi1D)    
flux_nonconservative_chan_etal(u_ll, u_rr, 
                               normal_ll::AbstractVector, normal_rr::AbstractVector,
                               equations::ShallowWaterEquationsQuasi1D)
```

Non-symmetric two-point volume flux discretizing the nonconservative (source) term that contains the gradient of the bottom topography [`ShallowWaterEquationsQuasi1D`](@ref)  and the channel width.

Further details are available in the paper:

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)   High order entropy stable schemes for the quasi-one-dimensional   shallow water and compressible Euler equations   [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
