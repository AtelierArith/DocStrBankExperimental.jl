Extension: VK_NV_ray_tracing

Arguments:

  * `type::VkAccelerationStructureTypeNV`
  * `geometries::Vector{_GeometryNV}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::VkBuildAccelerationStructureFlagsNV`: defaults to `0`
  * `instance_count::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureInfoNV.html)

```julia
_AccelerationStructureInfoNV(
    type::VulkanCore.LibVulkan.VkAccelerationStructureTypeKHR,
    geometries::AbstractArray;
    next,
    flags,
    instance_count
) -> Vulkan._AccelerationStructureInfoNV

```
