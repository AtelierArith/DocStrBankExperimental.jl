拡張: VK*EXT*discard_rectangles

引数:

  * `max_discard_rectangles::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDiscardRectanglePropertiesEXT.html)

```julia
_PhysicalDeviceDiscardRectanglePropertiesEXT(
    max_discard_rectangles::Integer;
    next
) -> Vulkan._PhysicalDeviceDiscardRectanglePropertiesEXT

```
