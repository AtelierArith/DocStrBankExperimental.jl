中間ラッパー VkSwapchainCreateInfoKHR。

拡張: VK*KHR*swapchain

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainCreateInfoKHR.html)

```julia
struct _SwapchainCreateInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSwapchainCreateInfoKHR`
  * `deps::Vector{Any}`
  * `surface::Vulkan.SurfaceKHR`
  * `old_swapchain::Union{Ptr{Nothing}, Vulkan.SwapchainKHR}`
