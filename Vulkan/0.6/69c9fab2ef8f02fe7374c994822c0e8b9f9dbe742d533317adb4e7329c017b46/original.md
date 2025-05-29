Extension: VK_EXT_multi_draw

Arguments:

  * `max_multi_draw_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiDrawPropertiesEXT.html)

```julia
_PhysicalDeviceMultiDrawPropertiesEXT(
    max_multi_draw_count::Integer;
    next
) -> Vulkan._PhysicalDeviceMultiDrawPropertiesEXT

```
