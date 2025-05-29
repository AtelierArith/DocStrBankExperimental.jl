拡張: VK*EXT*filter_cubic

引数:

  * `filter_cubic::Bool`
  * `filter_cubic_minmax::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFilterCubicImageViewImageFormatPropertiesEXT.html)

```julia
_FilterCubicImageViewImageFormatPropertiesEXT(
    filter_cubic::Bool,
    filter_cubic_minmax::Bool;
    next
) -> Vulkan._FilterCubicImageViewImageFormatPropertiesEXT

```
