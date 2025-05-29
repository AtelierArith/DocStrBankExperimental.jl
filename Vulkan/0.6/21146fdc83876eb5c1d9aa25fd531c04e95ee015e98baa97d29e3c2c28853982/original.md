High-level wrapper for VkPhysicalDeviceAccelerationStructureFeaturesKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceAccelerationStructureFeaturesKHR.html)

```julia
struct PhysicalDeviceAccelerationStructureFeaturesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `acceleration_structure::Bool`
  * `acceleration_structure_capture_replay::Bool`
  * `acceleration_structure_indirect_build::Bool`
  * `acceleration_structure_host_commands::Bool`
  * `descriptor_binding_acceleration_structure_update_after_bind::Bool`
