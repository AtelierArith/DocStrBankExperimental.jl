拡張機能: VK*EXT*swapchain_maintenance1

戻りコード:

  * `SUCCESS`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `device::Device`
  * `release_info::_ReleaseSwapchainImagesInfoEXT`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkReleaseSwapchainImagesEXT.html)

```julia
_release_swapchain_images_ext(
    device,
    release_info::Vulkan._ReleaseSwapchainImagesInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
