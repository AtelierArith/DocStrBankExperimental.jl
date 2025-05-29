拡張: VK*EXT*multi_draw

引数:

  * `max_multi_draw_count::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiDrawPropertiesEXT.html)

```julia
_PhysicalDeviceMultiDrawPropertiesEXT(
    max_multi_draw_count::Integer;
    next
) -> Vulkan._PhysicalDeviceMultiDrawPropertiesEXT

```
