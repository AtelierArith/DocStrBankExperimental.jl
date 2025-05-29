Extension: VK_EXT_swapchain_maintenance1

Arguments:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_indices::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkReleaseSwapchainImagesInfoEXT.html)

```julia
ReleaseSwapchainImagesInfoEXT(
    swapchain::Vulkan.SwapchainKHR,
    image_indices::AbstractArray;
    next
) -> Vulkan.ReleaseSwapchainImagesInfoEXT

```
