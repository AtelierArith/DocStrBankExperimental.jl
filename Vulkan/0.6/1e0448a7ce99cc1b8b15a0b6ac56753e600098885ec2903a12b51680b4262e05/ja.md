高レベルのラッパー VkCopyMemoryToAccelerationStructureInfoKHR。

拡張: VK*KHR*acceleration_structure

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToAccelerationStructureInfoKHR.html)

```julia
struct CopyMemoryToAccelerationStructureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.DeviceOrHostAddressConstKHR`
  * `dst::Vulkan.AccelerationStructureKHR`
  * `mode::Vulkan.CopyAccelerationStructureModeKHR`
