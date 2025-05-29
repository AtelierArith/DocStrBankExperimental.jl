拡張: VK*EXT*acquire*drm*display

戻り値コード:

  * `SUCCESS`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `physical_device::PhysicalDevice`
  * `drm_fd::Int32`
  * `display::DisplayKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireDrmDisplayEXT.html)

```julia
acquire_drm_display_ext(
    physical_device,
    drm_fd::Integer,
    display
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
