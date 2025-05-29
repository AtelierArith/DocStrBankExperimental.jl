拡張: VK*KHR*swapchain

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_SURFACE_LOST_KHR`
  * `ERROR_NATIVE_WINDOW_IN_USE_KHR`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_COMPRESSION_EXHAUSTED_EXT`

引数:

  * `device::Device`
  * `create_info::_SwapchainCreateInfoKHR` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSwapchainKHR.html)

```julia
_create_swapchain_khr(
    device,
    create_info::Vulkan._SwapchainCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.SwapchainKHR, Vulkan.VulkanError}

```
