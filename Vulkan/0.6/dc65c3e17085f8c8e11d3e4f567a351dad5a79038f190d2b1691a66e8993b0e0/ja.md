拡張: VK*EXT*sample_locations

引数:

  * `max_sample_location_grid_size::_Extent2D`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisamplePropertiesEXT.html)

```julia
_MultisamplePropertiesEXT(
    max_sample_location_grid_size::Vulkan._Extent2D;
    next
) -> Vulkan._MultisamplePropertiesEXT

```
