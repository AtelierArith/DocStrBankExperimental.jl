Extension: VK_KHR_get_display_properties2

Arguments:

  * `display_properties::_DisplayPropertiesKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayProperties2KHR.html)

```julia
_DisplayProperties2KHR(
    display_properties::Vulkan._DisplayPropertiesKHR;
    next
) -> Vulkan._DisplayProperties2KHR

```
