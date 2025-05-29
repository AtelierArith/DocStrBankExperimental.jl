High-level wrapper for VkBindImageMemoryDeviceGroupInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryDeviceGroupInfo.html)

```julia
struct BindImageMemoryDeviceGroupInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `device_indices::Vector{UInt32}`
  * `split_instance_bind_regions::Vector{Vulkan.Rect2D}`
