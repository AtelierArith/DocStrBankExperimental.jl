中間ラッパー VkCopyAccelerationStructureInfoKHR。

拡張: VK*KHR*acceleration_structure

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
struct _CopyAccelerationStructureInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyAccelerationStructureInfoKHR`
  * `deps::Vector{Any}`
  * `src::Vulkan.AccelerationStructureKHR`
  * `dst::Vulkan.AccelerationStructureKHR`
