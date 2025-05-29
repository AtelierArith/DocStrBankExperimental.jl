拡張: VK*EXT*opacity_micromap

引数:

  * `type::MicromapTypeEXT`
  * `mode::BuildMicromapModeEXT`
  * `data::DeviceOrHostAddressConstKHR`
  * `scratch_data::DeviceOrHostAddressKHR`
  * `triangle_array::DeviceOrHostAddressConstKHR`
  * `triangle_array_stride::UInt64`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::BuildMicromapFlagEXT`: デフォルトは `0`
  * `dst_micromap::MicromapEXT`: デフォルトは `C_NULL`
  * `usage_counts::Vector{MicromapUsageEXT}`: デフォルトは `C_NULL`
  * `usage_counts_2::Vector{MicromapUsageEXT}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildInfoEXT.html)

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
