拡張機能: VK*EXT*display_control

引数:

  * `device_event::DeviceEventTypeEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceEventInfoEXT.html)

```julia
_DeviceEventInfoEXT(
    device_event::Vulkan.DeviceEventTypeEXT;
    next
) -> Vulkan._DeviceEventInfoEXT

```
