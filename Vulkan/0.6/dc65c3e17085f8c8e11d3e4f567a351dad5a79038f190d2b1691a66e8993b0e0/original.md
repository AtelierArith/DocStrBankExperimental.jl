Extension: VK_EXT_sample_locations

Arguments:

  * `max_sample_location_grid_size::_Extent2D`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMultisamplePropertiesEXT.html)

```julia
_MultisamplePropertiesEXT(
    max_sample_location_grid_size::Vulkan._Extent2D;
    next
) -> Vulkan._MultisamplePropertiesEXT

```
