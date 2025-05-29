Extension: VK_EXT_border_color_swizzle

Arguments:

  * `border_color_swizzle::Bool`
  * `border_color_swizzle_from_image::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceBorderColorSwizzleFeaturesEXT.html)

```julia
_PhysicalDeviceBorderColorSwizzleFeaturesEXT(
    border_color_swizzle::Bool,
    border_color_swizzle_from_image::Bool;
    next
) -> Vulkan._PhysicalDeviceBorderColorSwizzleFeaturesEXT

```
