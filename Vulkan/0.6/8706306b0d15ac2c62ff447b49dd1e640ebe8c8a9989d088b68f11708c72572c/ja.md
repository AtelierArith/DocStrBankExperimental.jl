VkReleaseSwapchainImagesInfoEXTの高レベルラッパー。

拡張: VK*EXT*swapchain_maintenance1

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkReleaseSwapchainImagesInfoEXT.html)

```julia
struct ReleaseSwapchainImagesInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `swapchain::Vulkan.SwapchainKHR`
  * `image_indices::Vector{UInt32}`
