拡張: VK*EXT*acquire*drm*display

戻りコード:

  * `SUCCESS`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `drm_fd::Int32`
  * `connector_id::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDrmDisplayEXT.html)

```julia
_get_drm_display_ext(
    physical_device,
    drm_fd::Integer,
    connector_id::Integer
) -> ResultTypes.Result{Vulkan.DisplayKHR, Vulkan.VulkanError}

```
