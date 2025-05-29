Extension: VK_EXT_custom_border_color

Arguments:

  * `custom_border_color::_ClearColorValue`
  * `format::Format`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerCustomBorderColorCreateInfoEXT.html)

```julia
_SamplerCustomBorderColorCreateInfoEXT(
    custom_border_color::Vulkan._ClearColorValue,
    format::Vulkan.Format;
    next
) -> Vulkan._SamplerCustomBorderColorCreateInfoEXT

```
