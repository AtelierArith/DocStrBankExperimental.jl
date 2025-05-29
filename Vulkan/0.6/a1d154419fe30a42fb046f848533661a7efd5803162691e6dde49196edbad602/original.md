Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_SURFACE_LOST_KHR`
  * `ERROR_NATIVE_WINDOW_IN_USE_KHR`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_COMPRESSION_EXHAUSTED_EXT`

Arguments:

  * `device::Device`
  * `create_info::SwapchainCreateInfoKHR` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSwapchainKHR.html)

```julia
create_swapchain_khr(
    device,
    create_info::Vulkan.SwapchainCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.SwapchainKHR, Vulkan.VulkanError}

```
