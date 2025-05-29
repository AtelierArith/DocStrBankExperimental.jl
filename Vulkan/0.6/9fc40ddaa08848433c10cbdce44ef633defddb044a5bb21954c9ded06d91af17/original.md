Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `SUBOPTIMAL_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_OUT_OF_DATE_KHR`
  * `ERROR_SURFACE_LOST_KHR`
  * `ERROR_FULL_SCREEN_EXCLUSIVE_MODE_LOST_EXT`

Arguments:

  * `queue::Queue` (externsync)
  * `present_info::PresentInfoKHR` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueuePresentKHR.html)

```julia
queue_present_khr(
    queue,
    present_info::Vulkan.PresentInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
