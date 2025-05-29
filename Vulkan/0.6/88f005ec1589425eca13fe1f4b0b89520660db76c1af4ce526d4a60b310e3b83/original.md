Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `swapchain::SwapchainKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSwapchainImagesKHR.html)

```julia
get_swapchain_images_khr(
    device,
    swapchain
) -> ResultTypes.Result{Vector{Vulkan.Image}, Vulkan.VulkanError}

```
