Extension: VK_EXT_opacity_micromap

Arguments:

  * `type::MicromapTypeEXT`
  * `mode::BuildMicromapModeEXT`
  * `data::_DeviceOrHostAddressConstKHR`
  * `scratch_data::_DeviceOrHostAddressKHR`
  * `triangle_array::_DeviceOrHostAddressConstKHR`
  * `triangle_array_stride::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::BuildMicromapFlagEXT`: defaults to `0`
  * `dst_micromap::MicromapEXT`: defaults to `C_NULL`
  * `usage_counts::Vector{_MicromapUsageEXT}`: defaults to `C_NULL`
  * `usage_counts_2::Vector{_MicromapUsageEXT}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildInfoEXT.html)

```julia
_MicromapBuildInfoEXT(
    type::Vulkan.MicromapTypeEXT,
    mode::Vulkan.BuildMicromapModeEXT,
    data::Vulkan._DeviceOrHostAddressConstKHR,
    scratch_data::Vulkan._DeviceOrHostAddressKHR,
    triangle_array::Vulkan._DeviceOrHostAddressConstKHR,
    triangle_array_stride::Integer;
    next,
    flags,
    dst_micromap,
    usage_counts,
    usage_counts_2
) -> Vulkan._MicromapBuildInfoEXT

```
