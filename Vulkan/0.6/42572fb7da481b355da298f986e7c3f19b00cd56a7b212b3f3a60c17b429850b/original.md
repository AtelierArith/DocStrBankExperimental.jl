Extension: VK_EXT_descriptor_buffer

Arguments:

  * `descriptor_buffer::Bool`
  * `descriptor_buffer_capture_replay::Bool`
  * `descriptor_buffer_image_layout_ignored::Bool`
  * `descriptor_buffer_push_descriptors::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorBufferFeaturesEXT.html)

```julia
PhysicalDeviceDescriptorBufferFeaturesEXT(
    descriptor_buffer::Bool,
    descriptor_buffer_capture_replay::Bool,
    descriptor_buffer_image_layout_ignored::Bool,
    descriptor_buffer_push_descriptors::Bool;
    next
) -> Vulkan.PhysicalDeviceDescriptorBufferFeaturesEXT

```
