拡張: VK*KHR*shared*presentable*image

戻りコード:

  * `SUCCESS`
  * `SUBOPTIMAL_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_OUT_OF_DATE_KHR`
  * `ERROR_SURFACE_LOST_KHR`
  * `ERROR_FULL_SCREEN_EXCLUSIVE_MODE_LOST_EXT`

引数:

  * `device::Device`
  * `swapchain::SwapchainKHR` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSwapchainStatusKHR.html)

```julia
_get_swapchain_status_khr(
    device,
    swapchain
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
