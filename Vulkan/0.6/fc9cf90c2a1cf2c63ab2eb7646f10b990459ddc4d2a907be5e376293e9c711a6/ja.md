拡張: VK*EXT*opacity_micromap

引数:

  * `max_opacity_2_state_subdivision_level::UInt32`
  * `max_opacity_4_state_subdivision_level::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceOpacityMicromapPropertiesEXT.html)

```julia
_PhysicalDeviceOpacityMicromapPropertiesEXT(
    max_opacity_2_state_subdivision_level::Integer,
    max_opacity_4_state_subdivision_level::Integer;
    next
) -> Vulkan._PhysicalDeviceOpacityMicromapPropertiesEXT

```
