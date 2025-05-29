Extension: VK_KHR_swapchain

Arguments:

  * `device::Device`
  * `swapchain::SwapchainKHR` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySwapchainKHR.html)

```julia
_destroy_swapchain_khr(device, swapchain; allocator)

```
