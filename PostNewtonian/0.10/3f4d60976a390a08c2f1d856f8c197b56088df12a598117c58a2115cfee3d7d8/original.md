```
inertial_waveform!(storage, inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
inertial_waveform!(storage, inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

Evaluate the post-Newtonian waveform mode weights in the inertial frame for the given `inspiral` output by [`orbital_evolution`](@ref), using pre-allocated storage.

The storage is assumed to be the object returned from [`inertial_waveform_computation_storage`](@ref).  Other arguments are the same as in [`inertial_waveform`](@ref).
