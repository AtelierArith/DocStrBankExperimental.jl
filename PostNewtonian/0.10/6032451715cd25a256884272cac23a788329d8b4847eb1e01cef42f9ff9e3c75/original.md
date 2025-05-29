```
coorbital_waveform!(storage, inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
coorbital_waveform!(storage, inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

Evaluate the post-Newtonian waveform mode weights in the co-orbital frame for the given `inspiral` output by [`orbital_evolution`](@ref), using pre-allocated storage.

The storage is assumed to be the object returned from [`coorbital_waveform_computation_storage`](@ref).  Other arguments are the same as in [`coorbital_waveform`](@ref).
