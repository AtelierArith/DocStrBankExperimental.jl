VkCopyAccelerationStructureInfoKHRの高レベルラッパー。

拡張: VK*KHR*acceleration_structure

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
struct CopyAccelerationStructureInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src::Vulkan.AccelerationStructureKHR`
  * `dst::Vulkan.AccelerationStructureKHR`
  * `mode::Vulkan.CopyAccelerationStructureModeKHR`
