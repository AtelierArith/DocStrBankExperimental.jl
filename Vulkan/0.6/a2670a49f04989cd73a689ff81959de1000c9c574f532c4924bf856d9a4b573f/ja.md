VkPhysicalDeviceDeviceGeneratedCommandsPropertiesNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDeviceGeneratedCommandsPropertiesNV.html)

```julia
struct PhysicalDeviceDeviceGeneratedCommandsPropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_graphics_shader_group_count::UInt32`
  * `max_indirect_sequence_count::UInt32`
  * `max_indirect_commands_token_count::UInt32`
  * `max_indirect_commands_stream_count::UInt32`
  * `max_indirect_commands_token_offset::UInt32`
  * `max_indirect_commands_stream_stride::UInt32`
  * `min_sequences_count_buffer_offset_alignment::UInt32`
  * `min_sequences_index_buffer_offset_alignment::UInt32`
  * `min_indirect_commands_buffer_offset_alignment::UInt32`
