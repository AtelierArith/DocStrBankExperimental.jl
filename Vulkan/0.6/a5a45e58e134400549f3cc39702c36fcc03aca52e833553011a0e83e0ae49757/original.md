Extension: VK_EXT_display_control

Arguments:

  * `device_event::DeviceEventTypeEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceEventInfoEXT.html)

```julia
_DeviceEventInfoEXT(
    device_event::Vulkan.DeviceEventTypeEXT;
    next
) -> Vulkan._DeviceEventInfoEXT

```
