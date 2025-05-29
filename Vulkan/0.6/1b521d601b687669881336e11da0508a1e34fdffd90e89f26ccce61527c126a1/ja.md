高レベルのラッパー VkAccelerationStructureCreateInfoKHR。

拡張: VK*KHR*acceleration_structure

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoKHR.html)

```julia
struct AccelerationStructureCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `create_flags::Vulkan.AccelerationStructureCreateFlagKHR`
  * `buffer::Vulkan.Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `type::Vulkan.AccelerationStructureTypeKHR`
  * `device_address::UInt64`
