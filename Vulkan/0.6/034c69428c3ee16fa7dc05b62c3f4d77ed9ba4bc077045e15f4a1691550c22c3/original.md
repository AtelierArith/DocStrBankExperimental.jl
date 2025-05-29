Extension: VK_NV_ray_tracing

Arguments:

  * `type::VkAccelerationStructureTypeNV`
  * `geometries::Vector{GeometryNV}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::VkBuildAccelerationStructureFlagsNV`: defaults to `C_NULL`
  * `instance_count::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureInfoNV.html)

```julia
AccelerationStructureInfoNV(
    type::VulkanCore.LibVulkan.VkAccelerationStructureTypeKHR,
    geometries::AbstractArray;
    next,
    flags,
    instance_count
) -> Vulkan.AccelerationStructureInfoNV

```
