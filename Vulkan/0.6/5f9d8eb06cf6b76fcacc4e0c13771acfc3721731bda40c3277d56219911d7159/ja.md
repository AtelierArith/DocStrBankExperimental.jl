拡張: VK*EXT*acquire*xlib*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `physical_device::PhysicalDevice`
  * `dpy::Ptr{Display}`
  * `display::DisplayKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireXlibDisplayEXT.html)

```julia
acquire_xlib_display_ext(
    physical_device,
    dpy::Ptr{Nothing},
    display
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
