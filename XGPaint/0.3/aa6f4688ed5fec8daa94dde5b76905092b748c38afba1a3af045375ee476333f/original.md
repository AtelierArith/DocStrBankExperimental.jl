```
paint!(result_map, nu_obs, model, sources, fluxes_cen, fluxes_sat)
```

Paint a source catalog onto a map, recording the fluxes in `fluxes_cen` and `fluxes_sat`.

# Arguments:

  * `result_map::HealpixMap{T_map, RingOrder}`: Healpix map to paint
  * `nu_obs`: frequency in Hz
  * `model::AbstractCIBModel{T}`: source model parameters
  * `sources`: NamedTuple containing source information from generate_sources
  * `fluxes_cen::AbstractArray`: buffer for writing fluxes of centrals
  * `fluxes_sat::AbstractArray`: buffer for writing fluxes of satellites
