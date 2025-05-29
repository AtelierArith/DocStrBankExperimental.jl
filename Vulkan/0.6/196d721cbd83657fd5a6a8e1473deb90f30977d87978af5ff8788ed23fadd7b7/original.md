Extension: VK_EXT_device_memory_report

Arguments:

  * `flags::UInt32`
  * `type::DeviceMemoryReportEventTypeEXT`
  * `memory_object_id::UInt64`
  * `size::UInt64`
  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `heap_index::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceMemoryReportCallbackDataEXT.html)

```julia
DeviceMemoryReportCallbackDataEXT(
    flags::Integer,
    type::Vulkan.DeviceMemoryReportEventTypeEXT,
    memory_object_id::Integer,
    size::Integer,
    object_type::Vulkan.ObjectType,
    object_handle::Integer,
    heap_index::Integer;
    next
) -> Vulkan.DeviceMemoryReportCallbackDataEXT

```
