High-level wrapper for VkDeviceGroupPresentInfoKHR.

Extension: VK_KHR_swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupPresentInfoKHR.html)

```julia
struct DeviceGroupPresentInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `device_masks::Vector{UInt32}`
  * `mode::Vulkan.DeviceGroupPresentModeFlagKHR`
