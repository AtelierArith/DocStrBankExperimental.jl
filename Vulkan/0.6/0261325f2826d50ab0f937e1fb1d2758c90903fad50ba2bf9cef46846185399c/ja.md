拡張: VK*EXT*blend*operation*advanced

引数:

  * `advanced_blend_max_color_attachments::UInt32`
  * `advanced_blend_independent_blend::Bool`
  * `advanced_blend_non_premultiplied_src_color::Bool`
  * `advanced_blend_non_premultiplied_dst_color::Bool`
  * `advanced_blend_correlated_overlap::Bool`
  * `advanced_blend_all_operations::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceBlendOperationAdvancedPropertiesEXT.html)

```julia
PhysicalDeviceBlendOperationAdvancedPropertiesEXT(
    advanced_blend_max_color_attachments::Integer,
    advanced_blend_independent_blend::Bool,
    advanced_blend_non_premultiplied_src_color::Bool,
    advanced_blend_non_premultiplied_dst_color::Bool,
    advanced_blend_correlated_overlap::Bool,
    advanced_blend_all_operations::Bool;
    next
) -> Vulkan.PhysicalDeviceBlendOperationAdvancedPropertiesEXT

```
