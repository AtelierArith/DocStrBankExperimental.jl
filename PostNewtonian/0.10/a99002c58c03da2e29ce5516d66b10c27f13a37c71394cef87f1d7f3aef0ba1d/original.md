```
inertial_waveform_computation_storage(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
inertial_waveform_computation_storage(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

Construct storage needed to compute waveforms in the inertial frame without allocations.

This returns the storage for the waveforms themselves, storage used for computing the Wigner 𝔇 matrices, and for "in-place" multiplication.  The returned quantity can just be passed as the first argument to [`inertial_waveform!`](@ref) without being unpacked.

The meaning of the arguments is the same as in [`inertial_waveform`](@ref).
