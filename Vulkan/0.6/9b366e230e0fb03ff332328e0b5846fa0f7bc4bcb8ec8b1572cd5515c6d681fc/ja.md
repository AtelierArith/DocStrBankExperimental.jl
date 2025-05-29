拡張: VK*NV*ray_tracing

引数:

  * `type::AccelerationStructureMemoryRequirementsTypeNV`
  * `acceleration_structure::AccelerationStructureNV`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMemoryRequirementsInfoNV.html)

```julia
_AccelerationStructureMemoryRequirementsInfoNV(
    type::Vulkan.AccelerationStructureMemoryRequirementsTypeNV,
    acceleration_structure;
    next
) -> Vulkan._AccelerationStructureMemoryRequirementsInfoNV

```
