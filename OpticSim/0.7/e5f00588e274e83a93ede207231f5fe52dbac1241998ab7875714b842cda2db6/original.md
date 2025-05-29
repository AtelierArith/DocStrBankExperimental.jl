```
trace(assembly::LensAssembly{T}, r::OpticalRay{T}, temperature::T = 20.0, pressure::T = 1.0; trackrays = nothing, test = false)
```

Returns the ray as it exits the assembly in the form of a [`LensTrace`](@ref) object if it hits any element in the assembly, otherwise `nothing`. Recursive rays are offset by a small amount (`RAY_OFFSET`) to prevent it from immediately reintersecting the same lens element.

`trackrays` can be passed an empty vector to accumulate the `LensTrace` objects at each intersection of `ray` with a surface in the assembly.
