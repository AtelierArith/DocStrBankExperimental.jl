Extension: VK_EXT_discard_rectangles

Arguments:

  * `max_discard_rectangles::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDiscardRectanglePropertiesEXT.html)

```julia
_PhysicalDeviceDiscardRectanglePropertiesEXT(
    max_discard_rectangles::Integer;
    next
) -> Vulkan._PhysicalDeviceDiscardRectanglePropertiesEXT

```
