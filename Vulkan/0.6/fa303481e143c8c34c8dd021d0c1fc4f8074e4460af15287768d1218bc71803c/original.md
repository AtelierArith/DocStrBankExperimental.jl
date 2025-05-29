Extension: VK_KHR_acceleration_structure

Arguments:

  * `acceleration_structures::Vector{AccelerationStructureKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSetAccelerationStructureKHR.html)

```julia
_WriteDescriptorSetAccelerationStructureKHR(
    acceleration_structures::AbstractArray;
    next
) -> Vulkan._WriteDescriptorSetAccelerationStructureKHR

```
