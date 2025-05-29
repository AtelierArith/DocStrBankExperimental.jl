拡張: VK*EXT*swapchain_maintenance1

引数:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkReleaseSwapchainImagesInfoEXT.html)

```julia
_ReleaseSwapchainImagesInfoEXT(
    swapchain,
    image_indices::AbstractArray;
    next
) -> Vulkan._ReleaseSwapchainImagesInfoEXT

```
