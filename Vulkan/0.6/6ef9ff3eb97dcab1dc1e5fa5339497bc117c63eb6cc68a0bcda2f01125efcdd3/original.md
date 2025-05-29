Intermediate wrapper for VkReleaseSwapchainImagesInfoEXT.

Extension: VK_EXT_swapchain_maintenance1

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkReleaseSwapchainImagesInfoEXT.html)

```julia
struct _ReleaseSwapchainImagesInfoEXT <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkReleaseSwapchainImagesInfoEXT`
  * `deps::Vector{Any}`
  * `swapchain::Vulkan.SwapchainKHR`
