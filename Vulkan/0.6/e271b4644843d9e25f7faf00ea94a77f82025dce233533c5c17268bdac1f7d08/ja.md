VkPhysicalDeviceTexelBufferAlignmentPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTexelBufferAlignmentProperties.html)

```julia
struct PhysicalDeviceTexelBufferAlignmentProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `storage_texel_buffer_offset_alignment_bytes::UInt64`
  * `storage_texel_buffer_offset_single_texel_alignment::Bool`
  * `uniform_texel_buffer_offset_alignment_bytes::UInt64`
  * `uniform_texel_buffer_offset_single_texel_alignment::Bool`
