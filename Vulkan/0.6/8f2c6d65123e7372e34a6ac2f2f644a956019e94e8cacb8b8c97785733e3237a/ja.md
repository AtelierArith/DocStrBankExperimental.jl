拡張: VK*EXT*descriptor_buffer

引数:

  * `descriptor_buffer::Bool`
  * `descriptor_buffer_capture_replay::Bool`
  * `descriptor_buffer_image_layout_ignored::Bool`
  * `descriptor_buffer_push_descriptors::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDescriptorBufferFeaturesEXT.html)

```julia
_PhysicalDeviceDescriptorBufferFeaturesEXT(
    descriptor_buffer::Bool,
    descriptor_buffer_capture_replay::Bool,
    descriptor_buffer_image_layout_ignored::Bool,
    descriptor_buffer_push_descriptors::Bool;
    next
) -> Vulkan._PhysicalDeviceDescriptorBufferFeaturesEXT

```
