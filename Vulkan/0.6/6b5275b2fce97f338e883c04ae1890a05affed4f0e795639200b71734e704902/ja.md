VkAccelerationStructureBuildGeometryInfoKHRの高レベルラッパー。

拡張: VK*KHR*acceleration_structure

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildGeometryInfoKHR.html)

```julia
struct AccelerationStructureBuildGeometryInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.AccelerationStructureTypeKHR`
  * `flags::Vulkan.BuildAccelerationStructureFlagKHR`
  * `mode::Vulkan.BuildAccelerationStructureModeKHR`
  * `src_acceleration_structure::Union{Ptr{Nothing}, Vulkan.AccelerationStructureKHR}`
  * `dst_acceleration_structure::Union{Ptr{Nothing}, Vulkan.AccelerationStructureKHR}`
  * `geometries::Union{Ptr{Nothing}, Vector{Vulkan.AccelerationStructureGeometryKHR}}`
  * `geometries_2::Union{Ptr{Nothing}, Vector{Vulkan.AccelerationStructureGeometryKHR}}`
  * `scratch_data::Vulkan.DeviceOrHostAddressKHR`
