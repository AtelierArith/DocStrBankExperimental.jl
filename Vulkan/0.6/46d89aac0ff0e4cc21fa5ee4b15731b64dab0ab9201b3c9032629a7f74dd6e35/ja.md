拡張: VK*GOOGLE*display_timing

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `device::Device`
  * `swapchain::SwapchainKHR` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetRefreshCycleDurationGOOGLE.html)

```julia
_get_refresh_cycle_duration_google(
    device,
    swapchain
) -> ResultTypes.Result{Vulkan._RefreshCycleDurationGOOGLE, Vulkan.VulkanError}

```
