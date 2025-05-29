High-level wrapper for VkAccelerationStructureTrianglesOpacityMicromapEXT.

Extension: VK_EXT_opacity_micromap

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureTrianglesOpacityMicromapEXT.html)

```julia
struct AccelerationStructureTrianglesOpacityMicromapEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `index_type::Vulkan.IndexType`
  * `index_buffer::Vulkan.DeviceOrHostAddressConstKHR`
  * `index_stride::UInt64`
  * `base_triangle::UInt32`
  * `usage_counts::Union{Ptr{Nothing}, Vector{Vulkan.MicromapUsageEXT}}`
  * `usage_counts_2::Union{Ptr{Nothing}, Vector{Vulkan.MicromapUsageEXT}}`
  * `micromap::Vulkan.MicromapEXT`
