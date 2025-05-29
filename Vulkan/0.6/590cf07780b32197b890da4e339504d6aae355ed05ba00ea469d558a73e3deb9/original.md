Return a `PhysicalDeviceVulkan11Features` object with the provided `features` set to true.

```jldoctest
julia> PhysicalDeviceVulkan11Features(; next = C_NULL)
PhysicalDeviceVulkan11Features(next=Ptr{Nothing}(0x0000000000000000))

julia> PhysicalDeviceVulkan11Features(:multiview, :variable_pointers, next = C_NULL)
PhysicalDeviceVulkan11Features(next=Ptr{Nothing}(0x0000000000000000), multiview, variable_pointers)
```

```julia
PhysicalDeviceVulkan11Features(
    features::Symbol...;
    next
) -> Vulkan.PhysicalDeviceVulkan11Features

```
