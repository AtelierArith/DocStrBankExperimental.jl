VkAccelerationStructureGeometryInstancesDataKHRの高レベルラッパー。

拡張: VK*KHR*acceleration_structure

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryInstancesDataKHR.html)

```julia
struct AccelerationStructureGeometryInstancesDataKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `array_of_pointers::Bool`
  * `data::Vulkan.DeviceOrHostAddressConstKHR`
