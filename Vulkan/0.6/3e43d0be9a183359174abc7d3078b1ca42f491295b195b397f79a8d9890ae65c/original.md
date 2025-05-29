Find a queue index (starting at 0) from `physical_device` which matches the provided `queue_capabilities`.

```jldoctest
julia> find_queue_family(physical_device, QUEUE_COMPUTE_BIT & QUEUE_GRAPHICS_BIT)
0
```

```julia
find_queue_family(
    physical_device::Vulkan.PhysicalDevice,
    queue_capabilities::Vulkan.QueueFlag
) -> Int64

```
