Extension: VK_KHR_xlib_surface

Arguments:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`
  * `dpy::Ptr{Display}`
  * `visual_id::VisualID`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceXlibPresentationSupportKHR.html)

```julia
get_physical_device_xlib_presentation_support_khr(
    physical_device,
    queue_family_index::Integer,
    dpy::Ptr{Nothing},
    visual_id::UInt64
) -> Bool

```
