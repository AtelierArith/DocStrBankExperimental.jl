拡張: VK*KHR*present_wait

戻りコード:

  * `SUCCESS`
  * `TIMEOUT`
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
  * `present_id::UInt64`
  * `timeout::UInt64`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkWaitForPresentKHR.html)

```julia
_wait_for_present_khr(
    device,
    swapchain,
    present_id::Integer,
    timeout::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
