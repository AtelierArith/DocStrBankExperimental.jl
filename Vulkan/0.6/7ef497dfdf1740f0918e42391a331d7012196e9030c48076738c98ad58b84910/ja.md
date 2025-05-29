拡張: VK*KHR*swapchain

引数:

  * `device::Device`
  * `swapchain::SwapchainKHR` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySwapchainKHR.html)

```julia
_destroy_swapchain_khr(device, swapchain; allocator)

```
