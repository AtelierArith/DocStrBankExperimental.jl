High-level wrapper for VkWriteDescriptorSet.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSet.html)

```julia
struct WriteDescriptorSet <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `dst_set::Vulkan.DescriptorSet`
  * `dst_binding::UInt32`
  * `dst_array_element::UInt32`
  * `descriptor_count::UInt32`
  * `descriptor_type::Vulkan.DescriptorType`
  * `image_info::Vector{Vulkan.DescriptorImageInfo}`
  * `buffer_info::Vector{Vulkan.DescriptorBufferInfo}`
  * `texel_buffer_view::Vector{Vulkan.BufferView}`
