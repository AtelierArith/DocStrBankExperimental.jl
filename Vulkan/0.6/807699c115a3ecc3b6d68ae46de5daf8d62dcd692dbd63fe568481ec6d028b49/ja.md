VkDeviceGroupPresentCapabilitiesKHRの高レベルラッパー。

拡張: VK*KHR*swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupPresentCapabilitiesKHR.html)

```julia
struct DeviceGroupPresentCapabilitiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `present_mask::NTuple{32, UInt32}`
  * `modes::Vulkan.DeviceGroupPresentModeFlagKHR`
