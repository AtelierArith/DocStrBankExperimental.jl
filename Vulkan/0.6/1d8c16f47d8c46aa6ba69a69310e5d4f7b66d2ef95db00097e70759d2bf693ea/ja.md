拡張: VK*EXT*custom*border*color

引数:

  * `custom_border_color::ClearColorValue`
  * `format::Format`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerCustomBorderColorCreateInfoEXT.html)

```julia
SamplerCustomBorderColorCreateInfoEXT(
    custom_border_color::Vulkan.ClearColorValue,
    format::Vulkan.Format;
    next
) -> Vulkan.SamplerCustomBorderColorCreateInfoEXT

```
