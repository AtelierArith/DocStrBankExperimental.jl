```
trace(system::AbstractOpticalSystem{T}, ray::OpticalRay{T}; trackrays = nothing, test = false)
```

Traces `system` with `ray`, if `test` is enabled then fresnel reflections are disabled and the power distribution will not be correct. Returns either a [`LensTrace`](@ref) if the ray hits the detector or `nothing` otherwise.

`trackrays` can be passed an empty vector to accumulate the `LensTrace` objects at each intersection of `ray` with a surface in the system.
