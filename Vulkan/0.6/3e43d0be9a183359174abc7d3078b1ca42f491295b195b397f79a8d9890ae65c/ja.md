`physical_device`と提供された`queue_capabilities`が一致するキューインデックス（0から始まる）を見つけます。

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
