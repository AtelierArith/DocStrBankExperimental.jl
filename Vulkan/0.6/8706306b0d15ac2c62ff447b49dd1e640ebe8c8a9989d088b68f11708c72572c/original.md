High-level wrapper for VkReleaseSwapchainImagesInfoEXT.

Extension: VK_EXT_swapchain_maintenance1

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkReleaseSwapchainImagesInfoEXT.html)

```julia
struct ReleaseSwapchainImagesInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `swapchain::Vulkan.SwapchainKHR`
  * `image_indices::Vector{UInt32}`
