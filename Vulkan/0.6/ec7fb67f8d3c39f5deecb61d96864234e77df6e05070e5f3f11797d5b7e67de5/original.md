Extension: VK_KHR_xcb_surface

Arguments:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`
  * `connection::Ptr{xcb_connection_t}`
  * `visual_id::xcb_visualid_t`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceXcbPresentationSupportKHR.html)

```julia
get_physical_device_xcb_presentation_support_khr(
    physical_device,
    queue_family_index::Integer,
    connection::Ptr{Nothing},
    visual_id::UInt32
) -> Bool

```
