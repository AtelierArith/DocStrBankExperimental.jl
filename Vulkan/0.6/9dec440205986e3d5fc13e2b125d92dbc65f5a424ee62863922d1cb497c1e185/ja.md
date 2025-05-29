拡張: VK*KHR*swapchain

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `swapchain::SwapchainKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSwapchainImagesKHR.html)

```julia
_get_swapchain_images_khr(
    device,
    swapchain
) -> ResultTypes.Result{Vector{Vulkan.Image}, Vulkan.VulkanError}

```
