High-level wrapper for VkBindImageMemorySwapchainInfoKHR.

Extension: VK_KHR_swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemorySwapchainInfoKHR.html)

```julia
struct BindImageMemorySwapchainInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `swapchain::Vulkan.SwapchainKHR`
  * `image_index::UInt32`
