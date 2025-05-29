拡張: VK*KHR*wayland_surface

引数:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`
  * `display::Ptr{wl_display}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceWaylandPresentationSupportKHR.html)

```julia
get_physical_device_wayland_presentation_support_khr(
    physical_device,
    queue_family_index::Integer,
    display::Ptr{Nothing}
) -> Bool

```
