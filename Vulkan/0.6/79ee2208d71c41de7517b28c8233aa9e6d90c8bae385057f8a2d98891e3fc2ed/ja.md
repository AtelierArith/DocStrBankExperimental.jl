拡張: VK*EXT*opacity_micromap

引数:

  * `type::MicromapTypeEXT`
  * `mode::BuildMicromapModeEXT`
  * `data::_DeviceOrHostAddressConstKHR`
  * `scratch_data::_DeviceOrHostAddressKHR`
  * `triangle_array::_DeviceOrHostAddressConstKHR`
  * `triangle_array_stride::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::BuildMicromapFlagEXT`: デフォルトは `0`
  * `dst_micromap::MicromapEXT`: デフォルトは `C_NULL`
  * `usage_counts::Vector{_MicromapUsageEXT}`: デフォルトは `C_NULL`
  * `usage_counts_2::Vector{_MicromapUsageEXT}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildInfoEXT.html)

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
