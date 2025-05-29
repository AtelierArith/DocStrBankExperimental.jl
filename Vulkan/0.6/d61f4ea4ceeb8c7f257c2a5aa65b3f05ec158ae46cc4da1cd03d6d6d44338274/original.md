Extension: VK_EXT_color_write_enable

Arguments:

  * `color_write_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceColorWriteEnableFeaturesEXT.html)

```julia
_PhysicalDeviceColorWriteEnableFeaturesEXT(
    color_write_enable::Bool;
    next
) -> Vulkan._PhysicalDeviceColorWriteEnableFeaturesEXT

```
