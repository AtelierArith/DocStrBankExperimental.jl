Extension: VK_KHR_acceleration_structure

Arguments:

  * `acceleration_structures::Vector{AccelerationStructureKHR}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSetAccelerationStructureKHR.html)

```julia
WriteDescriptorSetAccelerationStructureKHR(
    acceleration_structures::AbstractArray;
    next
) -> Vulkan.WriteDescriptorSetAccelerationStructureKHR

```
