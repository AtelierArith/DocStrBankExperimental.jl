```
update_binned_map!(vec, skymap::PolarizedMap{T, O}, hitmap::Healpix.Map{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T <: Real, O <: Healpix.Order}
update_binned_map!(skymap::PolarizedMap{T, O}, hitmap::Healpix.Map{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T <: Real, O <: Healpix.Order}
update_binned_map!(skymap::PolarizedMap{T, O}, hitmap::Healpix.Map{T, O}, obs_list::Vector{Observation{T}}; comm=nothing, unseen=NaN) where {T <: Real, O <: Healpix.Order}
```

Apply Eqs. (18), (19), and (20) to compute the values of I, Q, and U from a TOD, and save the result in `skymap` and `hitmap`.

The three versions differ for the source of the TOD calibrated data:

  * if the `vec` parameter is present (first form), it will be used instead of `obs.tod` (second form)
  * instead of `obs` (a single [`Observation`](@ref) object), you can pass an array `obs_list` (third form). All the elements in this array will be used to update `skymap` and `hitmap`.
