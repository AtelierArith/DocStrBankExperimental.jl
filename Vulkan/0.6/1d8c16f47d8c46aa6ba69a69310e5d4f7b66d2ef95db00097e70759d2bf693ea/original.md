Extension: VK_EXT_custom_border_color

Arguments:

  * `custom_border_color::ClearColorValue`
  * `format::Format`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerCustomBorderColorCreateInfoEXT.html)

```julia
SamplerCustomBorderColorCreateInfoEXT(
    custom_border_color::Vulkan.ClearColorValue,
    format::Vulkan.Format;
    next
) -> Vulkan.SamplerCustomBorderColorCreateInfoEXT

```
