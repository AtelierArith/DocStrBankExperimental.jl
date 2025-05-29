Extension: VK_KHR_get_display_properties2

Arguments:

  * `display_mode_properties::_DisplayModePropertiesKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayModeProperties2KHR.html)

```julia
_DisplayModeProperties2KHR(
    display_mode_properties::Vulkan._DisplayModePropertiesKHR;
    next
) -> Vulkan._DisplayModeProperties2KHR

```
