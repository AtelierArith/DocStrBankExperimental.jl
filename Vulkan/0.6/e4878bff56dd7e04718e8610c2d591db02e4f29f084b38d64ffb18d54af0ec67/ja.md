拡張: VK*EXT*custom*border*color

引数:

  * `custom_border_color::_ClearColorValue`
  * `format::Format`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerCustomBorderColorCreateInfoEXT.html)

```julia
_SamplerCustomBorderColorCreateInfoEXT(
    custom_border_color::Vulkan._ClearColorValue,
    format::Vulkan.Format;
    next
) -> Vulkan._SamplerCustomBorderColorCreateInfoEXT

```
