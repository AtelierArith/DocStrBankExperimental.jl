VkAccelerationStructureBuildRangeInfoKHRの高レベルラッパー。

拡張: VK*KHR*acceleration_structure

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildRangeInfoKHR.html)

```julia
struct AccelerationStructureBuildRangeInfoKHR <: Vulkan.HighLevelStruct
```

  * `primitive_count::UInt32`
  * `primitive_offset::UInt32`
  * `first_vertex::UInt32`
  * `transform_offset::UInt32`
