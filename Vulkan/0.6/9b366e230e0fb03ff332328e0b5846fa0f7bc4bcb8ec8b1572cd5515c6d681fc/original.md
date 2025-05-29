Extension: VK_NV_ray_tracing

Arguments:

  * `type::AccelerationStructureMemoryRequirementsTypeNV`
  * `acceleration_structure::AccelerationStructureNV`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMemoryRequirementsInfoNV.html)

```julia
_AccelerationStructureMemoryRequirementsInfoNV(
    type::Vulkan.AccelerationStructureMemoryRequirementsTypeNV,
    acceleration_structure;
    next
) -> Vulkan._AccelerationStructureMemoryRequirementsInfoNV

```
