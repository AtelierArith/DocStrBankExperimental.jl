拡張: VK*NV*ray_tracing

引数:

  * `type::AccelerationStructureMemoryRequirementsTypeNV`
  * `acceleration_structure::AccelerationStructureNV`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMemoryRequirementsInfoNV.html)

```julia
AccelerationStructureMemoryRequirementsInfoNV(
    type::Vulkan.AccelerationStructureMemoryRequirementsTypeNV,
    acceleration_structure::Vulkan.AccelerationStructureNV;
    next
) -> Vulkan.AccelerationStructureMemoryRequirementsInfoNV

```
