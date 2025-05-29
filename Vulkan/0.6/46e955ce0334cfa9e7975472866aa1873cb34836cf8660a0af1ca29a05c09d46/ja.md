拡張: VK*EXT*opacity_micromap

引数:

  * `index_type::IndexType`
  * `index_buffer::_DeviceOrHostAddressConstKHR`
  * `index_stride::UInt64`
  * `base_triangle::UInt32`
  * `micromap::MicromapEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `usage_counts::Vector{_MicromapUsageEXT}`: デフォルトは `C_NULL`
  * `usage_counts_2::Vector{_MicromapUsageEXT}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureTrianglesOpacityMicromapEXT.html)

```julia
_AccelerationStructureTrianglesOpacityMicromapEXT(
    index_type::Vulkan.IndexType,
    index_buffer::Vulkan._DeviceOrHostAddressConstKHR,
    index_stride::Integer,
    base_triangle::Integer,
    micromap;
    next,
    usage_counts,
    usage_counts_2
) -> Vulkan._AccelerationStructureTrianglesOpacityMicromapEXT

```
