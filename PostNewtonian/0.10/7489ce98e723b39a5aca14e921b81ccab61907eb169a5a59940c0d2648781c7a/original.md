```
coorbital_waveform_computation_storage(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
coorbital_waveform_computation_storage(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

Construct storage needed to compute waveforms in the co-orbital frame without allocations.

This returns the storage for the waveforms themselves and `PNSystem` used as temporary storage.  The returned quantity can just be passed as the first argument to [`coorbital_waveform!`](@ref) without being unpacked.

The meaning of the arguments is the same as in [`coorbital_waveform`](@ref).
