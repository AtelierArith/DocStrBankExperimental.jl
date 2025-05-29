拡張: VK*KHR*display_swapchain

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INCOMPATIBLE_DISPLAY_KHR`
  * `ERROR_DEVICE_LOST`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `device::Device`
  * `create_infos::Vector{SwapchainCreateInfoKHR}` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSharedSwapchainsKHR.html)

```julia
create_shared_swapchains_khr(
    device,
    create_infos::AbstractArray;
    allocator
) -> ResultTypes.Result{Vector{Vulkan.SwapchainKHR}, Vulkan.VulkanError}

```
