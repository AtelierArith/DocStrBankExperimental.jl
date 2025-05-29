Extension: VK_NV_ray_tracing

Arguments:

  * `acceleration_structures::Vector{AccelerationStructureNV}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSetAccelerationStructureNV.html)

```julia
_WriteDescriptorSetAccelerationStructureNV(
    acceleration_structures::AbstractArray;
    next
) -> Vulkan._WriteDescriptorSetAccelerationStructureNV

```
