```
InPhaseSpacePoint
```

A partial type specialization on [`PhaseSpacePoint`](@ref) which can be used for dispatch in functions requiring only the in channel of the phase space to exist, for example implementations of `_incident_flux`. No restrictions are imposed on the out-channel, which may or may not exist.

See also: [`OutPhaseSpacePoint`](@ref)
