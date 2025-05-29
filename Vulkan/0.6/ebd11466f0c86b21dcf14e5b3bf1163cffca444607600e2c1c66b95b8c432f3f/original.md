Extension: VK_KHR_display_swapchain

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INCOMPATIBLE_DISPLAY_KHR`
  * `ERROR_DEVICE_LOST`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `device::Device`
  * `create_infos::Vector{_SwapchainCreateInfoKHR}` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSharedSwapchainsKHR.html)

```julia
_create_shared_swapchains_khr(
    device,
    create_infos::AbstractArray;
    allocator
) -> ResultTypes.Result{Vector{Vulkan.SwapchainKHR}, Vulkan.VulkanError}

```
