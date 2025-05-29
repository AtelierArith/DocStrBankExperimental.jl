引数:

  * `storage_texel_buffer_offset_alignment_bytes::UInt64`
  * `storage_texel_buffer_offset_single_texel_alignment::Bool`
  * `uniform_texel_buffer_offset_alignment_bytes::UInt64`
  * `uniform_texel_buffer_offset_single_texel_alignment::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTexelBufferAlignmentProperties.html)

```julia
_PhysicalDeviceTexelBufferAlignmentProperties(
    storage_texel_buffer_offset_alignment_bytes::Integer,
    storage_texel_buffer_offset_single_texel_alignment::Bool,
    uniform_texel_buffer_offset_alignment_bytes::Integer,
    uniform_texel_buffer_offset_single_texel_alignment::Bool;
    next
) -> Vulkan._PhysicalDeviceTexelBufferAlignmentProperties

```
