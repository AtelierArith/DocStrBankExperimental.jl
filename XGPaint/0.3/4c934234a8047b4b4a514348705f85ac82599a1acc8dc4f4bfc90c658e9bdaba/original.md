```
paint!(result_map, model, sources, min_redshift, max_redshift)
```

'Paint' the LRG catalog onto a map.

# Arguments:

  * `result_map::HealpixMap{T_map, RingOrder}`: Healpix map to paint
  * `model::AbstractCIBModel{T}`: source model parameters
  * `sources`: NamedTuple containing source information from generate_sources
  * `fluxes_cen::AbstractArray`: buffer for writing fluxes of centrals
  * `fluxes_sat::AbstractArray`: buffer for writing fluxes of satellites
