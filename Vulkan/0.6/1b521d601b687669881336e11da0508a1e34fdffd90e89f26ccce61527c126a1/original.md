High-level wrapper for VkAccelerationStructureCreateInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoKHR.html)

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
