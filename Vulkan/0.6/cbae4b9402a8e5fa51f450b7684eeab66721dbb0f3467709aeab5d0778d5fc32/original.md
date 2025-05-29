Extension: VK_NV_ray_tracing

Arguments:

  * `type::AccelerationStructureMemoryRequirementsTypeNV`
  * `acceleration_structure::AccelerationStructureNV`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMemoryRequirementsInfoNV.html)

```julia
AccelerationStructureMemoryRequirementsInfoNV(
    type::Vulkan.AccelerationStructureMemoryRequirementsTypeNV,
    acceleration_structure::Vulkan.AccelerationStructureNV;
    next
) -> Vulkan.AccelerationStructureMemoryRequirementsInfoNV

```
