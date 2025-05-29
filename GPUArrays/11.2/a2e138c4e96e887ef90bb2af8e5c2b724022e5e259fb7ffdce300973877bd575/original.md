```
AbstractDeviceArray{T, N} <: DenseArray{T, N}
```

Supertype for `N`-dimensional GPU arrays (or array-like types) with elements of type `T`. Instances of this type are expected to live on the device, see [`AbstractGPUArray`](@ref) for host-side objects.
