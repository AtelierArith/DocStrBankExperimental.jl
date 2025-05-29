拡張: VK*KHR*swapchain

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

  * `queue::Queue` (externsync)
  * `present_info::_PresentInfoKHR` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueuePresentKHR.html)

```julia
_queue_present_khr(
    queue,
    present_info::Vulkan._PresentInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
