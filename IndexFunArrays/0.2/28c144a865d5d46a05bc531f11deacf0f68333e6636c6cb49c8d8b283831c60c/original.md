```
phase_kz([T=Float64], size::NTuple{N, Int};
offset=CtrFT,
dims=ntuple(+, N),
scale=ScaFT,
weight=1,
accumulator=sum)
Calculates a propagation phase (without the 2pi factor!) for a z-step of one.
The relative sampling of `k_max_rel` you should supply `xy_scale = 2 ./ (k_max_rel .* sz[1:2])` as the scale argument.
To achieve Nyquist sampling for the complex field, i.e. the Ewald-circle touching the side of the array, this would be `scale=2 ./ sz[1:2]`.
The propagation equation uses 
Δz .* sqrt.(1-kxy_rel^2) as the propagation phase. Therefore the Z-propagation distance Δz has to be specified in units of the wavelength in the medium (`λ = n*λ₀`).
Note that since the phase is normalized to 1 instead of 2pi, you need to use this phase in the following sense: `cispi.(2.*phase_kz(...))`.
For other arguments look at similar scaler IndexFunArray functions such as rr.
```

See also: `propagator()`
