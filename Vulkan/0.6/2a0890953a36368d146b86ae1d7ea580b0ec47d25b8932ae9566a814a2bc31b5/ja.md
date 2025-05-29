拡張: VK*EXT*swapchain_maintenance1

引数:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_indices::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkReleaseSwapchainImagesInfoEXT.html)

```julia
ReleaseSwapchainImagesInfoEXT(
    swapchain::Vulkan.SwapchainKHR,
    image_indices::AbstractArray;
    next
) -> Vulkan.ReleaseSwapchainImagesInfoEXT

```
