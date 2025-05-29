拡張: VK*NV*ray_tracing

引数:

  * `type::VkAccelerationStructureTypeNV`
  * `geometries::Vector{GeometryNV}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::VkBuildAccelerationStructureFlagsNV`: デフォルトは `C_NULL`
  * `instance_count::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureInfoNV.html)

```julia
AccelerationStructureInfoNV(
    type::VulkanCore.LibVulkan.VkAccelerationStructureTypeKHR,
    geometries::AbstractArray;
    next,
    flags,
    instance_count
) -> Vulkan.AccelerationStructureInfoNV

```
