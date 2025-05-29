Extension: VK_EXT_acquire_xlib_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `dpy::Ptr{Display}`
  * `rr_output::RROutput`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetRandROutputDisplayEXT.html)

```julia
_get_rand_r_output_display_ext(
    physical_device,
    dpy::Ptr{Nothing},
    rr_output::UInt64
) -> ResultTypes.Result{Vulkan.DisplayKHR, Vulkan.VulkanError}

```
