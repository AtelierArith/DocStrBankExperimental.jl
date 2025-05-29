```
flux_chan_etal(u_ll, u_rr, orientation,
               equations::ShallowWaterEquationsQuasi1D)
```

Total energy conservative (mathematical entropy for quasi 1D shallow water equations) split form. When the bottom topography is nonzero this scheme will be well-balanced when used as a `volume_flux`. The `surface_flux` should still use, e.g., [`FluxPlusDissipation(flux_chan_etal, DissipationLocalLaxFriedrichs())`](@ref).

Further details are available in the paper:

  * Jesse Chan, Khemraj Shukla, Xinhui Wu, Ruofeng Liu, Prani Nalluri (2023)  High order entropy stable schemes for the quasi-one-dimensional shallow water and compressible Euler equations [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)
