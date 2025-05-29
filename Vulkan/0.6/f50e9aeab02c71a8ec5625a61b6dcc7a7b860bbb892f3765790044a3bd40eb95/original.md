Extension: VK_EXT_display_control

Arguments:

  * `display_event::DisplayEventTypeEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayEventInfoEXT.html)

```julia
_DisplayEventInfoEXT(
    display_event::Vulkan.DisplayEventTypeEXT;
    next
) -> Vulkan._DisplayEventInfoEXT

```
