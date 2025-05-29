Extension: VK_EXT_opacity_micromap

Arguments:

  * `micromap::Bool`
  * `micromap_capture_replay::Bool`
  * `micromap_host_commands::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceOpacityMicromapFeaturesEXT.html)

```julia
_PhysicalDeviceOpacityMicromapFeaturesEXT(
    micromap::Bool,
    micromap_capture_replay::Bool,
    micromap_host_commands::Bool;
    next
) -> Vulkan._PhysicalDeviceOpacityMicromapFeaturesEXT

```
