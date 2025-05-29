Extension: VK_KHR_get_display_properties2

Arguments:

  * `capabilities::_DisplayPlaneCapabilitiesKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneCapabilities2KHR.html)

```julia
_DisplayPlaneCapabilities2KHR(
    capabilities::Vulkan._DisplayPlaneCapabilitiesKHR;
    next
) -> Vulkan._DisplayPlaneCapabilities2KHR

```
