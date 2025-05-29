Extension: VK_GOOGLE_display_timing

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_OUT_OF_DATE_KHR`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `device::Device`
  * `swapchain::SwapchainKHR` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPastPresentationTimingGOOGLE.html)

```julia
get_past_presentation_timing_google(
    device,
    swapchain
) -> ResultTypes.Result{Vector{Vulkan.PastPresentationTimingGOOGLE}, Vulkan.VulkanError}

```
