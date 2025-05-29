拡張: VK*KHR*swapchain

戻りコード:

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

引数:

  * `device::Device`
  * `acquire_info::AcquireNextImageInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireNextImage2KHR.html)

```julia
acquire_next_image_2_khr(
    device,
    acquire_info::Vulkan.AcquireNextImageInfoKHR
) -> ResultTypes.Result{Tuple{UInt32, Vulkan.Result}, Vulkan.VulkanError}

```
