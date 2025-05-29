Arguments:

  * `max_inline_uniform_block_size::UInt32`
  * `max_per_stage_descriptor_inline_uniform_blocks::UInt32`
  * `max_per_stage_descriptor_update_after_bind_inline_uniform_blocks::UInt32`
  * `max_descriptor_set_inline_uniform_blocks::UInt32`
  * `max_descriptor_set_update_after_bind_inline_uniform_blocks::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceInlineUniformBlockProperties.html)

```julia
PhysicalDeviceInlineUniformBlockProperties(
    max_inline_uniform_block_size::Integer,
    max_per_stage_descriptor_inline_uniform_blocks::Integer,
    max_per_stage_descriptor_update_after_bind_inline_uniform_blocks::Integer,
    max_descriptor_set_inline_uniform_blocks::Integer,
    max_descriptor_set_update_after_bind_inline_uniform_blocks::Integer;
    next
) -> Vulkan.PhysicalDeviceInlineUniformBlockProperties

```
