```
inertial_waveform(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
inertial_waveform(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

Evaluate the post-Newtonian waveform mode weights in the inertial frame for the given `inspiral` output by [`orbital_evolution`](@ref).

The inertial frame is the one in which inertial observers are found, so this waveform is more like one that actual observers would detect.  This function transforms the waveform from the co-orbital frame — which is the one in which PN expressions are provided.

See [`coorbital_waveform`](@ref) for details about the other arguments and returned quantity.
