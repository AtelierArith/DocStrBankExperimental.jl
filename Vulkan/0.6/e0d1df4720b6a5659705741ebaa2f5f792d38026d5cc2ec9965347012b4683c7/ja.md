拡張: VK*NV*ray_tracing

引数:

  * `type::VkAccelerationStructureTypeNV`
  * `geometries::Vector{_GeometryNV}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::VkBuildAccelerationStructureFlagsNV`: デフォルトは `0`
  * `instance_count::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureInfoNV.html)

```julia
_AccelerationStructureInfoNV(
    type::VulkanCore.LibVulkan.VkAccelerationStructureTypeKHR,
    geometries::AbstractArray;
    next,
    flags,
    instance_count
) -> Vulkan._AccelerationStructureInfoNV

```
