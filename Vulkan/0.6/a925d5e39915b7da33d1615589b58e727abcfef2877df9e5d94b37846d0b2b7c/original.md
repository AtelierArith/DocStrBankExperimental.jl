High-level wrapper for VkDescriptorBufferBindingInfoEXT.

Extension: VK_EXT_descriptor_buffer

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferBindingInfoEXT.html)

```julia
struct DescriptorBufferBindingInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `address::UInt64`
  * `usage::Vulkan.BufferUsageFlag`
