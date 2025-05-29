Arguments:

  * `inline_uniform_block::Bool`
  * `descriptor_binding_inline_uniform_block_update_after_bind::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceInlineUniformBlockFeatures.html)

```julia
_PhysicalDeviceInlineUniformBlockFeatures(
    inline_uniform_block::Bool,
    descriptor_binding_inline_uniform_block_update_after_bind::Bool;
    next
) -> Vulkan._PhysicalDeviceInlineUniformBlockFeatures

```
