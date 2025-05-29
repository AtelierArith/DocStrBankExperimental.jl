Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `TIMEOUT`
  * `NOT_READY`
  * `SUBOPTIMAL_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_OUT_OF_DATE_KHR`
  * `ERROR_SURFACE_LOST_KHR`
  * `ERROR_FULL_SCREEN_EXCLUSIVE_MODE_LOST_EXT`

Arguments:

  * `device::Device`
  * `swapchain::SwapchainKHR` (externsync)
  * `timeout::UInt64`
  * `semaphore::Semaphore`: defaults to `C_NULL` (externsync)
  * `fence::Fence`: defaults to `C_NULL` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireNextImageKHR.html)

```julia
_acquire_next_image_khr(
    device,
    swapchain,
    timeout::Integer;
    semaphore,
    fence
) -> ResultTypes.Result{Tuple{UInt32, Vulkan.Result}, Vulkan.VulkanError}

```
