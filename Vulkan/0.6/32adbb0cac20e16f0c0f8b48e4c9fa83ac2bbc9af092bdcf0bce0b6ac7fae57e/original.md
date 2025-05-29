Return a `PhysicalDeviceVulkan13Features` object with the provided `features` set to true.

```jldoctest
julia> PhysicalDeviceVulkan13Features(; next = C_NULL)
PhysicalDeviceVulkan13Features(next=Ptr{Nothing}(0x0000000000000000))

julia> PhysicalDeviceVulkan13Features(:dynamic_rendering)
PhysicalDeviceVulkan13Features(next=Ptr{Nothing}(0x0000000000000000), dynamic_rendering)
```

```julia
PhysicalDeviceVulkan13Features(
    features::Symbol...;
    next
) -> Vulkan.PhysicalDeviceVulkan13Features

```
