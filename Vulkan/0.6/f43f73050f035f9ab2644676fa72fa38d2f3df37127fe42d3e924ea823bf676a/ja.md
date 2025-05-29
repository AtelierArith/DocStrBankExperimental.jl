高レベルのラッパー VkAcquireNextImageInfoKHR。

拡張: VK*KHR*swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireNextImageInfoKHR.html)

```julia
struct AcquireNextImageInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `swapchain::Vulkan.SwapchainKHR`
  * `timeout::UInt64`
  * `semaphore::Union{Ptr{Nothing}, Vulkan.Semaphore}`
  * `fence::Union{Ptr{Nothing}, Vulkan.Fence}`
  * `device_mask::UInt32`
