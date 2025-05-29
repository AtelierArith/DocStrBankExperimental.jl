Intermediate wrapper for VkGeneratedCommandsInfoNV.

Extension: VK_NV_device_generated_commands

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeneratedCommandsInfoNV.html)

```julia
struct _GeneratedCommandsInfoNV <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkGeneratedCommandsInfoNV`
  * `deps::Vector{Any}`
  * `pipeline::Vulkan.Pipeline`
  * `indirect_commands_layout::Vulkan.IndirectCommandsLayoutNV`
  * `preprocess_buffer::Vulkan.Buffer`
  * `sequences_count_buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `sequences_index_buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
