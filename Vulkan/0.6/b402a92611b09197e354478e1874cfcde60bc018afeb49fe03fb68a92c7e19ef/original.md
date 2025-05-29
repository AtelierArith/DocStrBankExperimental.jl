Return a `PhysicalDeviceFeatures` object with the provided `features` set to true.

```jldoctest
julia> PhysicalDeviceFeatures()
PhysicalDeviceFeatures()

julia> PhysicalDeviceFeatures(:wide_lines, :sparse_binding)
PhysicalDeviceFeatures(wide_lines, sparse_binding)
```

```julia
PhysicalDeviceFeatures(features::Symbol...) -> Any

```
