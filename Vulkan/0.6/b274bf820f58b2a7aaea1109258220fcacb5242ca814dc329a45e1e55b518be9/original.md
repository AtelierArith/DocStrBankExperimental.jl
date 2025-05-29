High-level wrapper for VkPresentInfoKHR.

Extension: VK_KHR_swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentInfoKHR.html)

```julia
struct PresentInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `wait_semaphores::Vector{Vulkan.Semaphore}`
  * `swapchains::Vector{Vulkan.SwapchainKHR}`
  * `image_indices::Vector{UInt32}`
  * `results::Union{Ptr{Nothing}, Vector{Vulkan.Result}}`
