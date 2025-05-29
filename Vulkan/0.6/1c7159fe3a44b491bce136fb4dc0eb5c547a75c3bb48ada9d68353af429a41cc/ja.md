拡張: VK*EXT*acquire*xlib*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `dpy::Ptr{Display}`
  * `rr_output::RROutput`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetRandROutputDisplayEXT.html)

```julia
get_rand_r_output_display_ext(
    physical_device,
    dpy::Ptr{Nothing},
    rr_output::UInt64
) -> ResultTypes.Result{Vulkan.DisplayKHR, Vulkan.VulkanError}

```
