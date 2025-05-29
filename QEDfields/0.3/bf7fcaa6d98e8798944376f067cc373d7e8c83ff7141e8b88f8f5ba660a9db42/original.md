```
envelope(pulsed_field::AbstractPulsedPlaneWaveField, phi::Real)
```

Return the value of the phase envelope function (also referred to as pulse envelope or pulse shape)  for given `pulsed_field` and phase `phi`. Performs domain check on `phi` before calling [`_envelope`](@ref);  returns zero if `phi` is not in the domain returned by `[domain](@ref)`.
