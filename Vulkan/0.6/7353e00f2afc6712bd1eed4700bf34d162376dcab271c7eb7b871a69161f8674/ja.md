拡張: VK*EXT*opacity_micromap

引数:

  * `micromap::Bool`
  * `micromap_capture_replay::Bool`
  * `micromap_host_commands::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceOpacityMicromapFeaturesEXT.html)

```julia
_PhysicalDeviceOpacityMicromapFeaturesEXT(
    micromap::Bool,
    micromap_capture_replay::Bool,
    micromap_host_commands::Bool;
    next
) -> Vulkan._PhysicalDeviceOpacityMicromapFeaturesEXT

```
