Extension: VK_EXT_opacity_micromap

Arguments:

  * `type::MicromapTypeEXT`
  * `mode::BuildMicromapModeEXT`
  * `data::DeviceOrHostAddressConstKHR`
  * `scratch_data::DeviceOrHostAddressKHR`
  * `triangle_array::DeviceOrHostAddressConstKHR`
  * `triangle_array_stride::UInt64`
  * `next::Any`: defaults to `C_NULL`
  * `flags::BuildMicromapFlagEXT`: defaults to `0`
  * `dst_micromap::MicromapEXT`: defaults to `C_NULL`
  * `usage_counts::Vector{MicromapUsageEXT}`: defaults to `C_NULL`
  * `usage_counts_2::Vector{MicromapUsageEXT}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildInfoEXT.html)

```julia
MicromapBuildInfoEXT(
    type::Vulkan.MicromapTypeEXT,
    mode::Vulkan.BuildMicromapModeEXT,
    data::Vulkan.DeviceOrHostAddressConstKHR,
    scratch_data::Vulkan.DeviceOrHostAddressKHR,
    triangle_array::Vulkan.DeviceOrHostAddressConstKHR,
    triangle_array_stride::Integer;
    next,
    flags,
    dst_micromap,
    usage_counts,
    usage_counts_2
) -> Vulkan.MicromapBuildInfoEXT

```
