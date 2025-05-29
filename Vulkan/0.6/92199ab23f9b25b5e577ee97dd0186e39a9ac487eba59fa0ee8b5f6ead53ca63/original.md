Extension: VK_EXT_opacity_micromap

Arguments:

  * `index_type::IndexType`
  * `index_buffer::DeviceOrHostAddressConstKHR`
  * `index_stride::UInt64`
  * `base_triangle::UInt32`
  * `micromap::MicromapEXT`
  * `next::Any`: defaults to `C_NULL`
  * `usage_counts::Vector{MicromapUsageEXT}`: defaults to `C_NULL`
  * `usage_counts_2::Vector{MicromapUsageEXT}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureTrianglesOpacityMicromapEXT.html)

```julia
AccelerationStructureTrianglesOpacityMicromapEXT(
    index_type::Vulkan.IndexType,
    index_buffer::Vulkan.DeviceOrHostAddressConstKHR,
    index_stride::Integer,
    base_triangle::Integer,
    micromap::Vulkan.MicromapEXT;
    next,
    usage_counts,
    usage_counts_2
) -> Vulkan.AccelerationStructureTrianglesOpacityMicromapEXT

```
