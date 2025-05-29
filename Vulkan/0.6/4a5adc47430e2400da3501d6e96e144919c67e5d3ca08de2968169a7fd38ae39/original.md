Extension: VK_EXT_blend_operation_advanced

Arguments:

  * `advanced_blend_max_color_attachments::UInt32`
  * `advanced_blend_independent_blend::Bool`
  * `advanced_blend_non_premultiplied_src_color::Bool`
  * `advanced_blend_non_premultiplied_dst_color::Bool`
  * `advanced_blend_correlated_overlap::Bool`
  * `advanced_blend_all_operations::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceBlendOperationAdvancedPropertiesEXT.html)

```julia
_PhysicalDeviceBlendOperationAdvancedPropertiesEXT(
    advanced_blend_max_color_attachments::Integer,
    advanced_blend_independent_blend::Bool,
    advanced_blend_non_premultiplied_src_color::Bool,
    advanced_blend_non_premultiplied_dst_color::Bool,
    advanced_blend_correlated_overlap::Bool,
    advanced_blend_all_operations::Bool;
    next
) -> Vulkan._PhysicalDeviceBlendOperationAdvancedPropertiesEXT

```
