拡張機能: VK*EXT*display_control

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_OUT_OF_DATE_KHR`

引数:

  * `device::Device`
  * `swapchain::SwapchainKHR`
  * `counter::SurfaceCounterFlagEXT`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSwapchainCounterEXT.html)

```julia
get_swapchain_counter_ext(
    device,
    swapchain,
    counter::Vulkan.SurfaceCounterFlagEXT
) -> ResultTypes.Result{UInt64, Vulkan.VulkanError}

```
