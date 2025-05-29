High-level wrapper for VkPhysicalDeviceDescriptorBufferFeaturesEXT.

Extension: VK_EXT_descriptor_buffer

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorBufferFeaturesEXT.html)

```julia
struct PhysicalDeviceDescriptorBufferFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `descriptor_buffer::Bool`
  * `descriptor_buffer_capture_replay::Bool`
  * `descriptor_buffer_image_layout_ignored::Bool`
  * `descriptor_buffer_push_descriptors::Bool`
