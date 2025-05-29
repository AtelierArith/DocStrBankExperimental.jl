Extension: VK_EXT_blend_operation_advanced

Arguments:

  * `src_premultiplied::Bool`
  * `dst_premultiplied::Bool`
  * `blend_overlap::BlendOverlapEXT`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendAdvancedStateCreateInfoEXT.html)

```julia
PipelineColorBlendAdvancedStateCreateInfoEXT(
    src_premultiplied::Bool,
    dst_premultiplied::Bool,
    blend_overlap::Vulkan.BlendOverlapEXT;
    next
) -> Vulkan.PipelineColorBlendAdvancedStateCreateInfoEXT

```
