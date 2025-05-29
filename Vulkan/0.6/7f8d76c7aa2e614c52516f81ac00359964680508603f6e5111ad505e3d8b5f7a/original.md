Extension: VK_EXT_border_color_swizzle

Arguments:

  * `components::_ComponentMapping`
  * `srgb::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerBorderColorComponentMappingCreateInfoEXT.html)

```julia
_SamplerBorderColorComponentMappingCreateInfoEXT(
    components::Vulkan._ComponentMapping,
    srgb::Bool;
    next
) -> Vulkan._SamplerBorderColorComponentMappingCreateInfoEXT

```
