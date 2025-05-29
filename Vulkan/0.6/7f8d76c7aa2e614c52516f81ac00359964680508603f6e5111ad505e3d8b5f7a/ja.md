拡張: VK*EXT*border*color*swizzle

引数:

  * `components::_ComponentMapping`
  * `srgb::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerBorderColorComponentMappingCreateInfoEXT.html)

```julia
_SamplerBorderColorComponentMappingCreateInfoEXT(
    components::Vulkan._ComponentMapping,
    srgb::Bool;
    next
) -> Vulkan._SamplerBorderColorComponentMappingCreateInfoEXT

```
