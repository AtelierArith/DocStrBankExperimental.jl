Extension: VK_EXT_filter_cubic

Arguments:

  * `filter_cubic::Bool`
  * `filter_cubic_minmax::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFilterCubicImageViewImageFormatPropertiesEXT.html)

```julia
_FilterCubicImageViewImageFormatPropertiesEXT(
    filter_cubic::Bool,
    filter_cubic_minmax::Bool;
    next
) -> Vulkan._FilterCubicImageViewImageFormatPropertiesEXT

```
