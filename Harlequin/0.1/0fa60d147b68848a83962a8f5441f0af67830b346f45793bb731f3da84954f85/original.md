```
compute_z_and_subgroup!(dest_baselines, vec, baseline_lengths, destriping_data::DestripingData{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
compute_z_and_subgroup!(dest_baselines, baseline_lengths, destriping_data::DestripingData{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
```

Compute the application of matrix $A$ in Eq. (25) in KurkiSuonio2009. The result is a set of baselines, and it is saved in `dest_baselines` (an array of elements whose type is `T`). The two forms differ only in the presence of the `vec` parameter: if it is not present, the value of `obs.tod` will be used.

This function only operates on single observations. If you want to apply it to an array of observations, use [`compute_z_and_group!`](@ref).
