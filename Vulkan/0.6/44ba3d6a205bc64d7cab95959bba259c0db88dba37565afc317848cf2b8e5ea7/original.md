Intermediate wrapper for VkAcquireNextImageInfoKHR.

Extension: VK_KHR_swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireNextImageInfoKHR.html)

```julia
struct _AcquireNextImageInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkAcquireNextImageInfoKHR`
  * `deps::Vector{Any}`
  * `swapchain::Vulkan.SwapchainKHR`
  * `semaphore::Union{Ptr{Nothing}, Vulkan.Semaphore}`
  * `fence::Union{Ptr{Nothing}, Vulkan.Fence}`
