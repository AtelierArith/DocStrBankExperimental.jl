Extension: VK_EXT_swapchain_maintenance1

Return codes:

  * `SUCCESS`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `device::Device`
  * `release_info::ReleaseSwapchainImagesInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkReleaseSwapchainImagesEXT.html)

```julia
release_swapchain_images_ext(
    device,
    release_info::Vulkan.ReleaseSwapchainImagesInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
