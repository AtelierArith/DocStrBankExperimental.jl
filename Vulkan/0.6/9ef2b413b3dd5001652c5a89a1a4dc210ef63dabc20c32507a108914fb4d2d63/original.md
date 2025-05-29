Arguments:

  * `storage_texel_buffer_offset_alignment_bytes::UInt64`
  * `storage_texel_buffer_offset_single_texel_alignment::Bool`
  * `uniform_texel_buffer_offset_alignment_bytes::UInt64`
  * `uniform_texel_buffer_offset_single_texel_alignment::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTexelBufferAlignmentProperties.html)

```julia
PhysicalDeviceTexelBufferAlignmentProperties(
    storage_texel_buffer_offset_alignment_bytes::Integer,
    storage_texel_buffer_offset_single_texel_alignment::Bool,
    uniform_texel_buffer_offset_alignment_bytes::Integer,
    uniform_texel_buffer_offset_single_texel_alignment::Bool;
    next
) -> Vulkan.PhysicalDeviceTexelBufferAlignmentProperties

```
