High-level wrapper for VkPhysicalDeviceDriverProperties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDriverProperties.html)

```julia
struct PhysicalDeviceDriverProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `driver_id::Vulkan.DriverId`
  * `driver_name::String`
  * `driver_info::String`
  * `conformance_version::Vulkan.ConformanceVersion`
