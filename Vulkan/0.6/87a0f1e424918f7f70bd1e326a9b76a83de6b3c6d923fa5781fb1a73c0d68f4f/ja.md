拡張: VK*EXT*blend*operation*advanced

引数:

  * `src_premultiplied::Bool`
  * `dst_premultiplied::Bool`
  * `blend_overlap::BlendOverlapEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendAdvancedStateCreateInfoEXT.html)

```julia
_PipelineColorBlendAdvancedStateCreateInfoEXT(
    src_premultiplied::Bool,
    dst_premultiplied::Bool,
    blend_overlap::Vulkan.BlendOverlapEXT;
    next
) -> Vulkan._PipelineColorBlendAdvancedStateCreateInfoEXT

```
