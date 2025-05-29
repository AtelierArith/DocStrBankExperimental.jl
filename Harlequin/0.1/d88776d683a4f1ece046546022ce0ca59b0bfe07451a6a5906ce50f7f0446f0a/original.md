```
compute_z_and_group!(dest_baselines, vectors, baseline_lengths, destriping_data::DestripingData{T, O}, obs_list::Vector{Observation{T}}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
compute_z_and_group!(dest_baselines, baseline_lengths, destriping_data::DestripingData{T, O}, obs_list::Vector{Observation{T}}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
```

Compute the application of matrix $A$ in Eq. (25) in KurkiSuonio2009. The result is a set of baselines, and it is saved in `dest_baselines` (an array of elements whose type is `T`). The two forms differ only in the presence of the `vec` parameter: if it is not present, the value of `obs.tod` will be used.
